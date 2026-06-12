---
title: "libc6 error  + buq"
date: 2005-05-26
forum: General Help
---

### Post by [pl]ice on 2005-05-26
can someone tell me what is this:
Inconsistency detected by ld.so: rtld.c: 1259: dl_main: Assertion `_rtld_local._dl_rtld_map.l_prev->l_next == _rtld_local._dl_rtld_map.l_next' failed!

i found that i can't run /libc.so.6 , so i changed the premissions, and when i run it i get that error. I google it and it cames out with a buq problem;

couple of my programs won't run when i call them from X, but will work under shell console call, would that be the problem??

albo i found that i don't have glibc; not in kynaptic either; do i need it? i downloaded it from debian ftp, but after reading all the info; well it looks skary to compile it, without damaging something else :D ...

EDIT:  i found that my progs won't run due to this problem :)

---

