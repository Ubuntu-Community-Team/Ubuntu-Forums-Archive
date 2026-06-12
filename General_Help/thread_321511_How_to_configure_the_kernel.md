---
title: "How to configure the kernel"
date: 2006-12-19
forum: General Help
---

### Post by LaoLiulaoliu on 2006-12-19
I want to configure the kernel 2.6.19.1
but  I don't know how to .

---

### Post by tkjacobsen on 2006-12-19
Here is a small howto that seems to work:
[http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065)



If you want to optimize the kernel for your own hardware use:
lspci: to see whats on you pci.
lshw: to see other hardware.
lsmod: to see which modules are running. You probably need those.




And one other thing: before make (x/menu)config you probably should copy the currend config and make your new with that as a base:

  cp /boot/config-`uname -r` /usr/src/linux/.config

---

### Post by LaoLiulaoliu on 2006-12-20
I have tried once ,but failed.

---

### Post by tkjacobsen on 2006-12-20
Have you installd build-essential and the appropriate linux-headers-* package? Linux-headers  is needet to "make oldconfig".. Build-essential to compile the kernel..

If you still have problems, post some more information here.

Good luck

---

### Post by tkjacobsen on 2006-12-20
Instead of "make oldconfig" you should use:

  cp /boot/config-`uname -r` /usr/src/linux/.config

---

