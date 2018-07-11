---
title: let Function
---
    
*let()* is a useful function defined in Kotlin standard library. It can be used for scoping and null-checks. 

<div class="sample" markdown="1">

```kotlin
import java.io.File

fun main(args: Array<String>) {
//sampleStart
File("input.txt").let {
    it.exists()                     // 1
}

var x: Int? = functionThatReturnsIntOrNull()
x = x ?. let {
    it + 2 // 2
} // 3

fun <A,B> applyUnlessNull(a: A?, f: (A) -> B) : B? =
    a ?. let { f(a) } // 4

//sampleEnd
}
```

</div>


1. file object is now accessible by reference `it`    
2. `it` is here guaranteed to be an ```Int```, not an ```Int?```
3. The whole expression evaluates to `x = null` if `x` is `null`, and `x = x+2` otherwise
4. `f` is only applied to `a` if `a` is not `null`.    
