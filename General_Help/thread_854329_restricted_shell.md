---
title: "restricted shell"
date: 2008-07-09
forum: General Help
---

### Post by sulekha on 2008-07-09
Hi,

this is what i have read in the book ubuntu linux unleashed,

if you have a desire to severly restrict what a user can do, you can provide him with a restricted shell. to run a restricted bash shell, you would use the -r option

ex:- bash -r

then try to do something that you could do as a regular user, such as ls -a,

you will then see

bash: ls: no such file or directory


now my question is suppose i have my shell restricted, how to make it back un restricted ?

---

### Post by lamego on 2008-07-09
bash -r will actually start a new shell on the restricted mode, you will just need to exit with "exit".

---

