---
title: "Komodo and Ubuntu"
date: 2005-07-13
forum: General Help
---

### Post by ubuntp on 2005-07-13
I've installed Komodo but the syntax checking won't work, please see below for the error. What lib do i have to install?


[IMG]http://www-public.rz.uni-duesseldorf.de/~thpod001/komodo.jpg[/IMG]

Maybe for future reference, i figured it out. 

apt-get install libstdc++2.10-glibc2.2
ln -s /usr/liblibstdc++-libc6.2-2.so.3 /usr/liblibstdc++-libc6.1-1.so.2

---

