---
title: "[SOLVED] System has crashed, please help"
date: 2008-04-13
forum: General Help
---

### Post by descentspb on 2008-04-13
I've launched an old and ugly sh script for x32 linux, and it changed the following libs in my /usr/libs directory (my system is x64):

libcrypto.so.0.9.7
libexpat.so.1
libpcre.so.3
libpcreposix.so.3
libssl.so.0.9.7

Now i have tons of bugs in my system. How can i restore them to native versions? Where can i get this libs? Thanks in advance.

---

### Post by descentspb on 2008-04-13
Solved the problem via apt-file search and apt-get install --reinstall

---

