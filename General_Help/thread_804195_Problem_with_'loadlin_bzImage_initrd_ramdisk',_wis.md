---
title: "Problem with 'loadlin bzImage initrd ramdisk', wish help"
date: 2008-05-22
forum: General Help
---

### Post by aijun2001 on 2008-05-22
I want to get start with linux image ank rootfs on a x86 machine,and on its' ram.
I enter :
loadlin bzImage ro root=/dev/ram initrd=initrd.img ramdisk_size=9216 vga=ask<Return>

System shows:
loading linux........
loading initrd.......
uncompressing linux .........

.......
details of loading....
.......
system goes until I got a message  like below:
partition check:
/dev/ide/host0/bus0/target0/lun0:p1 p2 <p5 p6 p7>

system halted.

wishing someone can help me,thank very much!!!

---

### Post by aijun2001 on 2008-05-27
it tell odds, because i chose so many functions when i'm compiling the kernel,this time i did a minimun kernel ,which is only suitable according to my work platform, booting period did not tell me odds.

---

