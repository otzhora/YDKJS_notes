Lexical scope means that scope is defined by author-time decisions of where functions are declared. The lexing phase of compilation is essentially able to know where and how all identifiers are declared, and thus predict how they will be looked-up during execution.

Two mechanisms in JavaScript can "cheat" lexical scope: `eval(..)` and `with`. The former can modify existing lexical scope (at runtime) by evaluating a string of "code" which has one or more declarations in it. The latter essentially creates a whole new lexical scope (again, at runtime) by treating an object reference _as_ a "scope" and that object's properties as scoped identifiers.

The downside to these mechanisms is that it defeats the _Engine_'s ability to perform compile-time optimizations regarding scope look-up, because the _Engine_ has to assume pessimistically that such optimizations will be invalid. Code _will_ run slower as a result of using either feature. **Don't use them.**
