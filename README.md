# Polymorphic Types and Collections Warm Up

This lab is to give you some practice in working with Java collections, polymorphism, generics, and, if you so choose: higher-order functions (these were added in Java8+). It's also an opportunity to gain some additional experience working in IntelliJ or the IDE of your choosing.

## Recalling Methods, Method-Level Generics

All the methods you will write should be marked `static`. A simple method is written below to help you recall the syntax:
```java
public static int add (int a, int b) { return a + b; }
```
An example of a method *parameterized* by two generic types might look like the following:
```java
public static <T, R> List<T> foo (R a) { ... } // generic 'type variables' here are T and R
```
And at the instruction/declaration:
```java
List<Integer> lst = foo(true); // infers that foo's generic T ~> Integer, R ~> Boolean (~> is 'substitued for')
 ```
Java's type system will automatically infer from the context that `T` should be substituted for Integer (since that's the type inside the declared type for variable `lst`) and `R` must be a boolean, since we pass the value `true` to method `foo`. Done explicitly, this would look like this:
```java
List<Integer> lst = <Integer, Boolean>foo(true);
 ```
 
 ## Required Methods

Implement each of the methods described below. When writing these methods, be sure to code to the interface (i.e. strive to use interface level types where possible).

**Note:** *for each method that has you return a list, be sure that this is a **new** list and not simply a mutated version of the passed-in parameter list.*

1. `lowerAll` should take a list of strings and return a *new list* of strings where each string passed is converted into lowercase. 
2. `add5` should take a list of integers and return a *new list* containing the elements of the original list with `5` added to each one. For example `add5(List.of(5, 4, 3, 5))` should return a list containing `[10, 9, 8, 10]`.
3. `convertToBools` write a method that takes a list of integers and returns a *new list* of booleans indicating `true` if the number at index *i* is positive (or zero); `false` otherwise. For example `convertToBools(List.of(1, -5, 6, 0, -1))` should return a list containing `[true, false, true, true, false]`.
4. Now add a `main` method and call each of these methods on different inputs and observe their various outputs (via print statements) to increase your confidence that you've implemented them correctly.

## Optional Challenge Problems

#### #1. Generalizing via Higher-Order Functions

Write a method, `app`, that generalizes the logic for questions 1, 2, and 3 from the previous section. Your method should 
be parameterized by two generic types: `T` and `R` and accept the following as formal parameters:
  * a list of `T` 
  * a function `f` that accepts an element of type `T` and produces an element of type `R` (i.e.: a `Function<T, R> f`)

The method should return a new list containing entries of type `R` (i.e.: those transformed by the function `f`). For example, here's how one might use this to solve the `add5` question without even needing to write an `add5` method:
```java
app(List.of(2, 5, 2, 5), (Integer e) -> e + 5); // returns the list [7, 10, 7, 10]
```
Note that one can construct a variable with a function type like so:
```java
Function<Integer, Integer> id = (Integer e) -> e;
```
The function shown is the identity function -- as it takes the input `e` and immediately gives it back unchanged (after the `->`).

#### #2. MSS

Write a method, `mss`, which takes an unordered array of ints (both positive and negative), and finds within the array a consecutive series of integers, which, when summed, is larger than any other consecutive sequence. E.g.:

```java
mss(new int[] {2, 3, -1, 10, -20, 7}) // should return 14
mss(new int[] {-4, 3, -3, 4, 3, -5})  // should return 7
mss(new int[] { })                    // should return 0
mss(new int[] {3, -4})                // should return 3
```
If you do attempt any of these challenges, make sure you test them in the `main(..)` method as you did in the previous section.

## Handin

When you are ready to submit, commit your work by typing:

> git commit -am "specific commit message goes here"

then follow this up with a

> git push origin main

Verify that your work has been successfully pushed to your online repo (the work showing up there should reflect your latest commit)
