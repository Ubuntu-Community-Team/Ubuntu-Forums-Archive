---
title: "VMGL Installation Questions"
date: 2007-08-27
forum: General Help
---

### Post by inthepit on 2007-08-27
I have been trying to decipher the instructions here: [http://www.cs.toronto.edu/~andreslc/xen-gl/](http://www.cs.toronto.edu/~andreslc/xen-gl/)

for installing vmgl in virtualbox for my linux vm.  anyone know if it works in virtualbox, or any other VM software.  I am willing to switch to Qemu or VMware if needed.

or if anyone has a howto or can write a howto for installation of VMGL in virtualbox on a feisty vm?

thanks

---

### Post by apetresc on 2007-08-27
According to the VMGL product page, > VMGL can be used on VMware guests, Xen HVM domains (depending on hardware virtualization extensions) and Xen paravirtual domains, using XVnc or the virtual framebuffer. Although we haven't tested it, VMGL should work for qemu, KVM, etc.
So if you switch to VMWare, you'll be golden for sure. Apparently qemu "should work" but hasn't been tested (you may want to try that first, since it's free, and report to the developers on what you got).

Since Virtualbox is not even mentioned as a "maybe", chances are good that it will not work at all.

---

### Post by ayllu on 2008-02-21
I reccomend Try it and tell us if its works, seems to be works but who knows, well is someone know how to get 3d in virtual machine please tell us or a good way to play all alll games. Cedega works but no for all games.

---

### Post by inthepit on 2008-02-21
one solution i have found requires a gaming pc running windows and a second pc running linux or windows.  [http://streammygame.com/smg/index.php](http://streammygame.com/smg/index.php)  but it isnt a vm solution unfortunately.

---

