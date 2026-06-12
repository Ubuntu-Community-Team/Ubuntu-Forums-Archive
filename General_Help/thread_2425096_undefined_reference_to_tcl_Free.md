---
title: "undefined reference to tcl_Free"
date: 2019-08-20
forum: General Help
---

### Post by jyotiranjan32 on 2019-08-20
I am getting below issue .

> 
/usr/lib/gcc/x86_64-linux-gnu/7/../../../x86_64-linux-gnu/libexpect.so: undefined reference to `Tcl_Free'
/usr/lib/gcc/x86_64-linux-gnu/7/../../../x86_64-linux-gnu/libexpect.so: undefined reference to `Tcl_ErrnoMsg'
/usr/lib/gcc/x86_64-linux-gnu/7/../../../x86_64-linux-gnu/libexpect.so: undefined reference to `Tcl_Alloc'


[COLOR=#000000]Has anybody seen this error before Please help me resolve it


[/COLOR]

---

### Post by TheFu on 2019-08-21
I haven't any clue, but did you install Tcl/TK?  Expect is built on those tools.  There are books on those languages.
I haven't seen expect used in a very long time. Most people have switched to devops tools like Ansible.

---

