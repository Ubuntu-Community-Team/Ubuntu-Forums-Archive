---
title: "How to avoid questions asked when using &quot;make oldconfig&quot;"
date: 2007-07-20
forum: General Help
---

### Post by fd9_ on 2007-07-20
Using "make oldconfig" when compiling the new kernel asks tons of questions, and I don't know how to answer most of them. Is there any way I can use default settings? I'm currently using Feisty and I'm trying to upgrade to the latest kernel (2.6.22.1).

---

### Post by tgcUbuntu on 2007-07-20
When you are n the /usr/src/linux directory do: sudo cp /boot/config-`uname -r` .config
This will copy the current configuration options to the current directory. Then do the sudo make oldconfig.

---

### Post by strabes on 2007-07-21
Or just hold enter through them all. That's what I do at least.

---

