---
title: "Cant compile or gcc error :( PLEASE"
date: 2007-04-20
forum: General Help
---

### Post by lynxus on 2007-04-20
Hi guys, Im trying to get ssh2 installed.

However when i do a ./configure i get this error :

root@broken-trumpet:/home/gsmart/Downloads/ssh-3.2.9.1# ./configure
checking for gcc... gcc
checking for gcc... gcc
checking whether the C compiler (gcc -g ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
root@broken-trumpet:/home/gsmart/Downloads/ssh-3.2.9.1# 

I have installed this fine on other installations even on the beta of this 7.4 release.

Any ideas? Im all out.

---

### Post by lynxus on 2007-04-20
Resolved:

Needed to install
# apt-get install build-essential

---

