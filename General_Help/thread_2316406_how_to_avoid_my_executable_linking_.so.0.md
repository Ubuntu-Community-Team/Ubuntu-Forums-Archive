---
title: "how to avoid my executable linking .so.0"
date: 2016-03-07
forum: General Help
---

### Post by newcfd on 2016-03-07
I am using third party libraries. The libraries generated from cmake do not have ending so.0.
But my executable is always compiled to link the so.0. I used softlink and did not have luck.
How can I change makefile to link my executable to so, not so.0.  Is there any flag for this?
Thanks for your help!

---

### Post by SeijiSensei on 2016-03-08
Have you tried copying the compiled libraries to libname.so.0?

---

