---
title: "LaTeX: File `T1.def' not found"
date: 2008-02-27
forum: General Help
---

### Post by guano on 2008-02-27
Hello all.

I'm trying to compile a LaTeX document which contains some Icelandic characters. At first, I noticed that the problem was related with the "eth" symbol, created with the command \dh. So I changed the encoding to T1, using

```
\usepackage[T1]{inputenc}
```

Now I have an error msg saying; 

```
/usr/share/texmf-texlive/tex/latex/base/inputenc.sty:128:File `T1.def' not found. \endinput
```

I've been looking around, installed a lot of latex-related packages, but without any luck. Can someone point out which is the package I am missing?

thanks

---

### Post by mali2297 on 2008-02-27
I think it should be
```

\usepackage[T1]{fontenc}

```

---

### Post by guano on 2008-02-27
Good Ho!

So simple it hurts! 

Many thanks man.

---

