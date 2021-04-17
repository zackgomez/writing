# In favor of `private` over `#` for private class properties in Typescript

## Background

Typescript provides two ways of creating private class properties.

* `private` is a keyword solving a compile time problem of throwing a compile time error when accessing a private class property outside of the class.
*   
* `#` is a naming constraint solving a runtime problem of throwing a runtime error when accessing a private class property outside of the class.

Our project does not need nor benefit from this runtime behavior, and therefore we should evaluate these two constructs by their compile time behavior.

## Evaluation

### Argument from authority
When Typescript chose to add private class properties, it added the `private` keyword.  Presumably, the team evaluated this to be the best solution to solving their compile time problem.  The ECMAScript committee is solving a different problem with `#` and came up with a different solution.

### Flexibility
Runtime constraints impose that `#` must at run time tell which variables are private, hence requiring the name of the variable to encode this information.  It fruther constrains accessing private variables to only `obj.#private` and not `obj['#private']`.

### Consistency

Typescript has no languages features that encode information in a variable name. `#` is therefore unique as a language construct.  As an example we use `let` and `const` keywords rather than naming variables differently.  `static` is a keyword used to modify class properties in both ECMAScript and Typescript.  `private` is more consistent with existing language features than `#`.

### Terseness
Terseness is not a terminal value, it is an instrumental value towards readability.  Terser code, all things equal, is more readable.  However, terser code can be less readable, and would be worse.  As an example, we don't use single letter variable names though they are terser.  Typescript doesn't use keywords that may be terser than others, `con` instead of `const`.

## Conclusion

The compile time behavior of `private` is superior to that of `#` for creating private class properties.  `private` is more consistent with existing language features and `#` brings with it no benefits at compile time.



## Links

https://github.com/tc39/proposal-class-fields/blob/master/PRIVATE_SYNTAX_FAQ.md
