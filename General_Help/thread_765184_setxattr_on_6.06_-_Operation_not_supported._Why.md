---
title: "setxattr on 6.06 - Operation not supported. Why?"
date: 2008-04-24
forum: General Help
---

### Post by fxtech on 2008-04-24
I have some code that sets some extended attributes on some directories, which previously worked on a CentOS distro. I'm not trying it on a fairly stock ubuntu 6.06 x64 machine, and I'm getting ENOSUP (operation not supported) when I try to *set* an attribute. I can call listxattr() but it always returns 0.

Is there some magic sauce to make this work? :confused:

---

