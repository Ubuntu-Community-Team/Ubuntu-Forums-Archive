---
title: "/usr/include directory problem"
date: 2007-10-30
forum: General Help
---

### Post by FIONEX on 2007-10-30
Hi

Whenever I try to include anything in my projects, it says "header not found".  For example, I copied code directly off the xubuntu website "#include <libxfce4panel/xfce-panel-window.h>" and tried to build it with no luck.  If I add the subdirectory "#include <xfce4/libxfce4panel/xfce-panel-window.h>" then it works, but all the headers that xfce4-panel-window.h includes will not be found.  What is the solution?  Why isn't it looking up subdirectories?  Why is there such blatant bugs in ubuntu?

---

### Post by Thyme on 2007-10-30
Hi FIONEX,

[[COLOR="blue"]This Link[/COLOR]]("http://xfc.xfce.org/docs/tutorial/html/index.html") shows how to build programs written for XFCE. It's C++ with XFCE I'm pretty sure that the headers are the same and the building + linking part as well.

But from my (very little experience) I think that you're not passing the correct xfce cflags and libs to gcc ..

---

