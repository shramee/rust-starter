# rust-starter

## Setup

1. Set up these directories.

```sh
mkdir t1-get-started
mkdir t2-basic-programming
mkdir t3-ownership
mkdir t4-data-and-pattern
mkdir t5-error-handling
mkdir t6-sample-project
```

Get Started on Rust
----------------------------

### Installation

-   Go to https://rustup.rs/ to install rust.
-   Install [rust-analyser](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer).

### Write Your First Rust Program

-   Hello World! example in Rust.
-   Compiling and running a Rust program.
-   Code snippet:

```rust
fn main() {
    println!("Hello, Rust!");
}
```

Basic Rust Programming Concepts
----------------------------------------

### Variables and Mutability

-   Variables and scopes
-   Mutability and shadowing
-   Code snippet:

```rust
fn main() {
    // Immutable
    let x = 5;

    // Mutable
    let mut y = 10;
    y = 20;

    // Shadowing immutable
    let x = 5;
}
```

### Data Types

-   Overview of basic data types (integer, floating-point, boolean, character).
-   Explanation of type inference.
-   Code snippet:

```rust
fn main() {
    let number: i32 = 42;
    let pi: f64 = 3.14159;
    let is_rust_fun: bool = true;
    let heart_emoji: char = '❤';
}
```

### Functions

-   How to define and call functions in Rust.
-   Function parameters and return values.
-   Code snippet:

```rust
fn add(x: i32, y: i32) -> i32 {
    x + y
}

fn main() {
    let result = add(5, 7);
}
```

### Control Structures

-   Introduction to if, else if, and else statements.
-   Code snippet:

```rust
fn main() {
    let number = 42;

    if number > 50 {
        println!("Greater than 50");
    } else if number < 50 {
        println!("Less than 50");
    } else {
        println!("Equal to 50");
    }
}
```

### Loops

-   Explanation of loop, while, and for loops in Rust.
-   Code snippet:

```rust
fn main() {
    let mut count = 0;

    while count < 5 {
        println!("Count: {}", count);
        count += 1;
    }

    for num in 1..=5 {
        println!("Number: {}", num);
    }
}
```

Ownership in Rust
--------------------------

### Ownership Principles

-   Explanation of ownership, borrowing, and lifetimes.
-   How Rust manages memory and avoids common programming errors.

### Ownership Rules

-   Each value has a single owner, 
-   Values are freed when the owner goes out of scope.

### Ownership - Memory Allocation

-   Explanation of Stack vs. Heap memory allocation.
-   How Rust manages memory allocation with ownership.

### References and Borrowing

-   Introduction to references and borrowing in Rust.
-   Mutable and immutable references.
-   Code snippet:

```rust
fn main() {
    let x = 42;
    let y = &x; // Immutable reference
    let mut z = 10;
    let w = &mut z; // Mutable reference
}
```

### Race Conditions

-   Discussion of race conditions in concurrent programming.
-   How Rust's ownership system prevents race conditions.

### Slices

-   Explanation of slices in Rust for working with parts of arrays or other collections.
-   Code snippet:

```rust
fn main() {
    let numbers = [1, 2, 3, 4, 5];
    let slice = &numbers[1..4];
}
```

Data Handling and Pattern Matching in Rust
---------------------------------------------------

### Structs

-   Introduction to structs in Rust for creating custom data types.
-   Code snippet:

```rust
struct Person {
    name: String,
    age: u32,
}

fn main() {
    let person = Person {
        name: String::from("Alice"),
        age: 30,
    };
}
```

### Methods

-   How to define methods for structs.
-   Code snippet:

```rust
struct Circle {
    radius: f64,
}

impl Circle {
    fn area(&self) -> f64 {
        3.14159 * self.radius * self.radius
    }
}
```

### Enums

-   Explanation of enums in Rust for defining custom data types.
-   Code snippet:

```rust
enum Color {
    Red,
    Green,
    Blue,
}

fn main() {
    let color = Color::Red;
}
```

### Pattern Matching

-   How to use pattern matching to handle different enum variants.
-   Code snippet:

```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter,
}

fn value_in_cents(coin: Coin) -> u32 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}
```

Error Handling
-----------------------

### Unrecoverable Errors with Panic

-   Introduction to panic! macro for handling unrecoverable errors.
-   Example of using panic for critical errors.

```rust
fn main() {
    let divisor = 0;
    let result = 42 / divisor; // This will panic!
}
```

### Recoverable Errors with Result - Introduction

-   Introduction to the Result enum for handling recoverable errors.
-   The Result type and its variants (Ok and Err).

```rust
fn main() -> Result<(), String> {
    let denominator = 0;
    if denominator == 0 {
        return Err("Denominator cannot be zero".to_string());
    }
    let result = 42 / denominator;
    Ok(())
}
```

### Recoverable Errors with Result - Demonstration

-   A more detailed example of using Result to handle errors.
-   Demonstrating error propagation with Result.

```rust
fn divide(a: i32, b: i32) -> Result<i32, String> {
    if b == 0 {
        return Err("Division by zero".to_string());
    }
    Ok(a / b)
}

fn main() {
    let result = divide(42, 0);
    match result {
        Ok(value) => println!("Result: {}", value),
        Err(error) => println!("Error: {}", error),
    }
}
```

Sample Rust Project
----------------------------

### Getting User Input

-   How to get user input using the `std::io` module.
-   Reading and parsing user input.

```rust
use std::io;

fn main() {
    let mut input = String::new();
    io::stdin().read_line(&mut input).expect("Failed to read input");
    let number: i32 = input.trim().parse().expect("Invalid input");
}
```

### Generating a Secret Number

-   Generating a random secret number using the `rand` crate.
-   Adding the crate to your project and using it.

```rust
extern crate rand;

use rand::Rng;

fn main() {
    let secret_number = rand::thread_rng().gen_range(1..=100);
}
```

### Comparing Guess to Secret Number

-   Getting user guesses and comparing them to the secret number.
-   Implementing a simple guessing game logic.

```rust
fn main() {
    let secret_number = rand::thread_rng().gen_range(1..=100);
    loop {
        // Get user input and compare with secret_number
        // Display appropriate messages based on the comparison
    }
}
```

### Allowing Multiple Guesses

-   Extending the guessing game to allow multiple guesses with a loop.
-   Keeping track of the number of attempts.

```rust
fn main() {
    let secret_number = rand::thread_rng().gen_range(1..=100);
    let mut attempts = 0;
    loop {
        attempts += 1;
        // Get user input, compare with secret_number, and manage game logic
    }
}
```
