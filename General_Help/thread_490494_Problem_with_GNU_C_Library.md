---
title: "Problem with GNU C Library"
date: 2007-07-02
forum: General Help
---

### Post by cluelessCS on 2007-07-02
Hi

Trying to install Sicstus Prolog, this error occured:

> 
Checking installation cache... install.cache
dummy.c:1:19: error: stdio.h: No such file or directory
dummy.c:2:30: error: gnu/libc-version.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:1:19: error: stdio.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:2:22: error: features.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c: In function ‘main’:
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:13: warning: incompatible implicit declaration of built-in function ‘printf’
Glibc header files and runtime system disagree on version.
Header files: x86-linux


Assuming it had something to with glibc, I re-installed libc6 dev via Synaptic. Still didn't work, the error just changed slightly, stating now that my glibc header files are version 2.4, while the runtime is 2.5

Here are my two questions:

(1) What can be the reason for this glibc 'disagree on version' error?

(2) The Sicstus Prolog that I downloaded says it requires glibc 2.3. Is it possible to install it on Ubuntu, with its higher glibc version, anyway?

---

