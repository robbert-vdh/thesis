# Annotating Deeply Embedded Languages

This is my master's thesis on extending deeply embedded
languages[\*](#deeply-embedded-language) with additional information that can be
used to add source mapping support and custom compiler instructions to existing
embedded languages.

Abstract:

> This thesis explores the idea of annotating deeply embedded languages with
> additional information. A common problem with deeply embedded languages is
> that there is no strong connection between an embedded program, the abstract
> syntax tree for that embedded program, and a compiled version of the program.
> By gathering source location information for embedded expressions using a
> novel implicit parameter-based approach and annotating the embedded program's
> AST with this information, it becomes possible to map the embedded program
> back to the original source code. This new information can be used to improve
> compiler diagnostics, and to provide better profiling and debugging
> experiences for the language. In addition, the idea of extending that approach
> by also annotating the language with instructions for the compiler as a way to
> allow the programmer to hand optimize parts of a program will be explored.
> Storing these instructions as annotations on the abstract syntax trees enables
> new optimization workflows without requiring any changes to the language
> itself. Finally, an implementation of this annotation system in an existing
> language is examined, and its consequences on the experience of using the
> language are evaluated.

[Full PDF](./annotating-deeply-embedded-languages.pdf)  
[Thesis defense presentation](https://github.com/robbert-vdh/thesis/blob/master/thesis-defense/index.html), presented by @tmcdonell at the [Haskell Implementor's Workshop 2022](https://youtu.be/2KNkl7W8Rok)

<sup id="deeply-embedded-language">
  *An embedded language is a programming language whose programs are written
  inside of another language, called the host language. Evaluating a shallowly
  embedded program directly produces a result, while deep embeddings
  produce an Abstract Syntax Tree of the program instead. This AST can then be
  checked, optimized, and eventually interpreted or compiled to native code.
</sup>

## Links

[ICFP 2022](https://icfp22.sigplan.org/details/hiw-2022/3/Annotating-Deeply-Embedded-Languages)  
[UU Theses Repository](https://studenttheses.uu.nl/handle/20.500.12932/41633)

## Implementation source code

The implementation for the annotation system as implemented in
[Accelerate](https://github.com/AccelerateHS/accelerate) can be found in the
GitHub repositories for the forked
[`accelerate`](https://github.com/robbert-vdh/accelerate/tree/feature/force-inline)
and the
[`accelerate-llvm`](https://github.com/robbert-vdh/accelerate-llvm/tree/feature/tracy-annotations)
packages. The
[`Data.Array.Accelerate.Annotations`](https://github.com/robbert-vdh/accelerate/blob/feature/force-inline/src/Data/Array/Accelerate/Annotations.hs)
module in the `accelerate` fork contains a complete guide on how to migrate
Accelerate libraries to the new annotated version of Accelerate. Take a look at
the
[`linear-accelerate`](https://github.com/robbert-vdh/linear-accelerate/tree/feature/annotations)
fork for an example on how to do this.
