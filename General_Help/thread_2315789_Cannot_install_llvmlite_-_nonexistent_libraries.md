---
title: "Cannot install llvmlite - nonexistent libraries?"
date: 2016-03-02
forum: General Help
---

### Post by GQDQALC on 2016-03-02
When I try to do sudo pip install llvmlite, I come up with the errors
```
/usr/bin/ld: cannot find -ledit
/usr/bin/ld: cannot find -lLLVMOProfileJIT

```

I have llvm-3.7 installed on Ubuntu 14.04. llvm-config --libs doesn't show either of these libraries. Any idea what's going on?

---

### Post by florian-geigl on 2016-03-04
hi - I'm struggling with almost the same problem. Pip can't find -lLLVMOProfileJIT and it's also not listed in llvm-config --libs. I tried installing llvm-3.7.0 and llvm-3.7.1 (because in the llvmlite docs they say it only works with 3.7 - so I'm not sure if this includes 3.7.1). Using 3.7.0 I instantly get a compilation error (tried g++ 4.9 and 5.3). If you were able to solve your problem it would be nice if you could post your solution. [COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by GQDQALC on 2016-03-07
Nope, still nothing :( Bump?

---

### Post by GQDQALC on 2016-03-13
Solved by installing conda

---

### Post by florian-geigl on 2016-03-14
just "solved" it yesterday using the same way... it would still be cool if one could really solve it ;)

---

