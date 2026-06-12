---
title: "Terminal ding on completion?"
date: 2008-05-04
forum: General Help
---

### Post by jorwex on 2008-05-04
is there a way to make the Terminal notify you when it's finished? specifically, i've been testing different versions of wine and it takes a 1/2 hour or so to do the "make depend && make" stage of compiling. I'd love for the terminal to *DING* when its finished so I don't have to keep checking it as I do other things on my computer.
Thanks,

Jordan

---

### Post by koenn on 2008-05-04
append ' && sleep 1 && echo -e \\a ' to your commands, eg here with ls :
```
ls && sleep 1 && echo -e \\a
```
the sleep isn't strictly necessary.

---

