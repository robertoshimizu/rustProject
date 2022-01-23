# Rust Programming Language

## Installation

If you’re using Linux or macOS, open a terminal and enter the following command:

```bash
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

The command downloads a script and starts the installation of the `rustup` tool, which installs the latest stable version of Rust. You might be prompted for your password. If the install is successful, the following line will appear:

```bash
Rust is installed now. Great!
```

After you’ve installed Rust via `rustup`, updating to the latest version is easy. From your shell, run the following update script:

```bash
rustup update
```

To check whether you have Rust installed correctly, open a shell and enter this line:

```bash
rustc --version
```

### Local Documentation

The installation of Rust also includes a copy of the documentation locally, so you can read it offline. Run `rustup doc` to open the local documentation in your browser.

## Writing and Running a Rust Program

Next, make a new source file and call it _main.rs_. Rust files always end with the .rs extension. If you’re using more than one word in your filename, use an underscore to separate them. For example, use _hello_world.rs_ rather than _helloworld.rs_.

On Linux or macOS, enter the following commands to compile and run the file:

```bash
rustc main.rs
./main
Hello, world!
```

## Using Cargo to manage the Rust Project

Cargo is Rust’s build system and package manager. Cargo comes installed with Rust. Check whether Cargo is installed by entering the following into your terminal:

```bash
cargo --version
```

### Creating a Project with Cargo

```bash
cargo new hello_cargo
cd hello_cargo
```

The first command creates a new directory called _hello_cargo_. We’ve named our project _hello_cargo_, and Cargo creates its files in a directory of the same name.

You’ll see that Cargo has generated two files and one directory for us: a `Cargo.toml` file and a `src` directory with a _main.rs_ file inside. It has also initialized a new Git repository along with a `.gitignore` file.

### Building and Running a Cargo Project

From your _hello_cargo_ directory, build your project by entering the following command:

```bash
cargo build
```

This command creates an executable file in _target/debug/hello_cargo_.
You can run the executable with this command:

```bash
./target/debug/hello_cargo
```

If all goes well, Hello, world! should print to the terminal. Running cargo build for the first time also causes Cargo to create a new file at the top level: _Cargo.lock_. This file keeps track of the exact versions of dependencies in your project.

We can also use cargo run to compile the code and then run the resulting executable all in one command:

```bash
cargo run
```

Cargo also provides a command called `cargo check`. This command quickly checks your code to make sure it compiles but doesn’t produce an executable:

```bash
cargo check
```

Often, `cargo check` is much faster than `cargo build`, because it skips the step of producing an executable. If you’re continually checking your work while writing the code, using `cargo check` will speed up the process! As such, many _Rustaceans_ run `cargo check` periodically as they write their program to make sure it compiles. Then they run `cargo build` when they’re ready to use the executable.

### Building for Release

When your project is finally ready for release, you can use `cargo build --release` to compile it with optimizations. This command will create an executable in _target/release_ instead of _target/debug_. The optimizations make your Rust code run faster, but turning them on lengthens the time it takes for your program to compile. This is why there are two different profiles: one for development, when you want to rebuild quickly and often, and another for building the final program you’ll give to a user that won’t be rebuilt repeatedly and that will run as fast as possible. If you’re benchmarking your code’s running time, be sure to run `cargo build --release` and benchmark with the executable in _target/release_.
