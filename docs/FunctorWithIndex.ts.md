---
title: FunctorWithIndex.ts
nav_order: 38
---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [FunctorWithIndex](#functorwithindex)
- [FunctorWithIndex1](#functorwithindex1)
- [FunctorWithIndex2](#functorwithindex2)
- [FunctorWithIndex2C](#functorwithindex2c)
- [FunctorWithIndex3](#functorwithindex3)
- [FunctorWithIndex3C](#functorwithindex3c)
- [FunctorWithIndex4](#functorwithindex4)
- [FunctorWithIndexComposition](#functorwithindexcomposition)
- [FunctorWithIndexComposition11](#functorwithindexcomposition11)
- [FunctorWithIndexComposition12](#functorwithindexcomposition12)
- [FunctorWithIndexComposition12C](#functorwithindexcomposition12c)
- [FunctorWithIndexComposition21](#functorwithindexcomposition21)
- [FunctorWithIndexComposition22](#functorwithindexcomposition22)
- [FunctorWithIndexComposition22C](#functorwithindexcomposition22c)
- [FunctorWithIndexComposition2C1](#functorwithindexcomposition2c1)
- [FunctorWithIndexComposition3C1](#functorwithindexcomposition3c1)
- [getFunctorWithIndexComposition](#getfunctorwithindexcomposition)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# FunctorWithIndex

A `FunctorWithIndex` is a type constructor which supports a mapping operation `mapWithIndex`.

`mapWithIndex` can be used to turn functions `i -> a -> b` into functions `f a -> f b` whose argument and return types use the type
constructor `f` to represent some computational context.

Instances must satisfy the following laws:

1. Identity: `F.mapWithIndex(fa, (_i, a) => a) = fa`
2. Composition: `F.mapWithIndex(fa, (_i, a) => bc(ab(a))) = F.mapWithIndex(F.mapWithIndex(fa, ab), bc)`

**Signature** (interface)

```ts
export interface FunctorWithIndex<F, I> extends Functor<F> {
  readonly mapWithIndex: <A, B>(fa: HKT<F, A>, f: (i: I, a: A) => B) => HKT<F, B>
}
```

Added in v1.12.0

# FunctorWithIndex1

**Signature** (interface)

```ts
export interface FunctorWithIndex1<F extends URIS, I> extends Functor1<F> {
  readonly mapWithIndex: <A, B>(fa: Type<F, A>, f: (i: I, a: A) => B) => Type<F, B>
}
```

# FunctorWithIndex2

**Signature** (interface)

```ts
export interface FunctorWithIndex2<F extends URIS2, I> extends Functor2<F> {
  readonly mapWithIndex: <L, A, B>(fa: Type2<F, L, A>, f: (i: I, a: A) => B) => Type2<F, L, B>
}
```

# FunctorWithIndex2C

**Signature** (interface)

```ts
export interface FunctorWithIndex2C<F extends URIS2, I, L> extends Functor2C<F, L> {
  readonly mapWithIndex: <A, B>(fa: Type2<F, L, A>, f: (i: I, a: A) => B) => Type2<F, L, B>
}
```

# FunctorWithIndex3

**Signature** (interface)

```ts
export interface FunctorWithIndex3<F extends URIS3, I> extends Functor3<F> {
  readonly mapWithIndex: <U, L, A, B>(fa: Type3<F, U, L, A>, f: (i: I, a: A) => B) => Type3<F, U, L, B>
}
```

# FunctorWithIndex3C

**Signature** (interface)

```ts
export interface FunctorWithIndex3C<F extends URIS3, I, U, L> extends Functor3C<F, U, L> {
  readonly mapWithIndex: <A, B>(fa: Type3<F, U, L, A>, f: (i: I, a: A) => B) => Type3<F, U, L, B>
}
```

# FunctorWithIndex4

**Signature** (interface)

```ts
export interface FunctorWithIndex4<F extends URIS4, I> extends Functor4<F> {
  readonly mapWithIndex: <X, U, L, A, B>(fa: Type4<F, X, U, L, A>, f: (i: I, a: A) => B) => Type4<F, X, U, L, B>
}
```

# FunctorWithIndexComposition

**Signature** (interface)

```ts
export interface FunctorWithIndexComposition<F, FI, G, GI> extends FunctorComposition<F, G> {
  readonly mapWithIndex: <A, B>(fga: HKT<F, HKT<G, A>>, f: (i: [FI, GI], a: A) => B) => HKT<F, HKT<G, B>>
}
```

# FunctorWithIndexComposition11

**Signature** (interface)

```ts
export interface FunctorWithIndexComposition11<F extends URIS, FI, G extends URIS, GI>
  extends FunctorComposition11<F, G> {
  readonly mapWithIndex: <A, B>(fa: Type<F, Type<G, A>>, f: (i: [FI, GI], a: A) => B) => Type<F, Type<G, B>>
}
```

# FunctorWithIndexComposition12

**Signature** (interface)

```ts
export interface FunctorWithIndexComposition12<F extends URIS, FI, G extends URIS2, GI>
  extends FunctorComposition12<F, G> {
  readonly mapWithIndex: <L, A, B>(fa: Type<F, Type2<G, L, A>>, f: (i: [FI, GI], a: A) => B) => Type<F, Type2<G, L, B>>
}
```

# FunctorWithIndexComposition12C

**Signature** (interface)

```ts
export interface FunctorWithIndexComposition12C<F extends URIS, FI, G extends URIS2, GI, L>
  extends FunctorComposition12C<F, G, L> {
  readonly mapWithIndex: <A, B>(fa: Type<F, Type2<G, L, A>>, f: (i: [FI, GI], a: A) => B) => Type<F, Type2<G, L, B>>
}
```

# FunctorWithIndexComposition21

**Signature** (interface)

```ts
export interface FunctorWithIndexComposition21<F extends URIS2, FI, G extends URIS, GI>
  extends FunctorComposition21<F, G> {
  readonly mapWithIndex: <L, A, B>(fa: Type2<F, L, Type<G, A>>, f: (i: [FI, GI], a: A) => B) => Type2<F, L, Type<G, B>>
}
```

# FunctorWithIndexComposition22

**Signature** (interface)

```ts
export interface FunctorWithIndexComposition22<F extends URIS2, FI, G extends URIS2, GI>
  extends FunctorComposition22<F, G> {
  readonly mapWithIndex: <L, M, A, B>(
    fa: Type2<F, L, Type2<G, M, A>>,
    f: (i: [FI, GI], a: A) => B
  ) => Type2<F, L, Type2<G, M, B>>
}
```

# FunctorWithIndexComposition22C

**Signature** (interface)

```ts
export interface FunctorWithIndexComposition22C<F extends URIS2, FI, G extends URIS2, GI, LG>
  extends FunctorComposition22C<F, G, LG> {
  readonly mapWithIndex: <L, A, B>(
    fa: Type2<F, L, Type2<G, LG, A>>,
    f: (i: [FI, GI], a: A) => B
  ) => Type2<F, L, Type2<G, LG, B>>
}
```

# FunctorWithIndexComposition2C1

**Signature** (interface)

```ts
export interface FunctorWithIndexComposition2C1<F extends URIS2, FI, G extends URIS, GI, L>
  extends FunctorComposition2C1<F, G, L> {
  readonly mapWithIndex: <A, B>(fa: Type2<F, L, Type<G, A>>, f: (i: [FI, GI], a: A) => B) => Type2<F, L, Type<G, B>>
}
```

# FunctorWithIndexComposition3C1

**Signature** (interface)

```ts
export interface FunctorWithIndexComposition3C1<F extends URIS3, FI, G extends URIS, GI, UF, LF>
  extends FunctorComposition3C1<F, G, UF, LF> {
  readonly mapWithIndex: <A, B>(
    fa: Type3<F, UF, LF, Type<G, A>>,
    f: (i: [FI, GI], a: A) => B
  ) => Type3<F, UF, LF, Type<G, B>>
}
```

# getFunctorWithIndexComposition

**Signature** (function)

```ts
export function getFunctorWithIndexComposition<F extends URIS3, FI, G extends URIS, GI, U, L>(
  F: FunctorWithIndex3C<F, FI, U, L>,
  G: FunctorWithIndex1<G, FI>
): FunctorWithIndexComposition3C1<F, FI, G, GI, U, L>
export function getFunctorWithIndexComposition<F extends URIS2, FI, G extends URIS2, GI, L>(
  F: FunctorWithIndex2<F, FI>,
  G: FunctorWithIndex2C<G, FI, L>
): FunctorWithIndexComposition22C<F, FI, G, GI, L>
export function getFunctorWithIndexComposition<F extends URIS2, FI, G extends URIS2, GI>(
  F: FunctorWithIndex2<F, FI>,
  G: FunctorWithIndex2<G, FI>
): FunctorWithIndexComposition22<F, FI, G, GI>
export function getFunctorWithIndexComposition<F extends URIS2, FI, G extends URIS, GI, L>(
  F: FunctorWithIndex2C<F, FI, L>,
  G: FunctorWithIndex1<G, GI>
): FunctorWithIndexComposition2C1<F, FI, G, GI, L>
export function getFunctorWithIndexComposition<F extends URIS2, FI, G extends URIS, GI>(
  F: FunctorWithIndex2<F, FI>,
  G: FunctorWithIndex1<G, GI>
): FunctorWithIndexComposition21<F, FI, G, GI>
export function getFunctorWithIndexComposition<F extends URIS, FI, G extends URIS2, GI, L>(
  F: FunctorWithIndex1<F, FI>,
  G: FunctorWithIndex2C<G, GI, L>
): FunctorWithIndexComposition12C<F, FI, G, GI, L>
export function getFunctorWithIndexComposition<F extends URIS, FI, G extends URIS2, GI>(
  F: FunctorWithIndex1<F, FI>,
  G: FunctorWithIndex2<G, GI>
): FunctorWithIndexComposition12<F, FI, G, GI>
export function getFunctorWithIndexComposition<F extends URIS, FI, G extends URIS, GI>(
  F: FunctorWithIndex1<F, FI>,
  G: FunctorWithIndex1<G, GI>
): FunctorWithIndexComposition11<F, FI, G, GI>
export function getFunctorWithIndexComposition<F, FI, G, GI>(
  F: FunctorWithIndex<F, FI>,
  G: FunctorWithIndex<G, GI>
): FunctorWithIndexComposition<F, FI, G, GI>
export function getFunctorWithIndexComposition<F, FI, G, GI>(
  F: FunctorWithIndex<F, FI>,
  G: FunctorWithIndex<G, GI>
): FunctorWithIndexComposition<F, FI, G, GI> { ... }
```

Added in v1.12.0
