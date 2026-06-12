---
title: "Help fixing Grub from command line please"
date: 2007-02-26
forum: General Help
---

### Post by Julian David Pitt on 2007-02-26
[COLOR="Blue"]I seem to have broken grub whilst trying to install vmware. I now get an error 17 saying unrecognised partition when I try to boot in Edgy. If I use the super grub boot disk I can boot ok but I do not want to have to use this every time I boot up. I know there are commands to sort this out as I have had to do it before, but of course I cannot remember the details. Thanks in advance. [/COLOR]

---

### Post by bodhi.zazen on 2007-02-26
Use the super grub boot disk to re-install grub to you MBR

---

### Post by Maestro23 on 2007-02-26
Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Julian David Pitt on 2007-02-26
Thanks but I have already tried the super grub disk, it will get my system to boot but it will not boot without the disk. I am getting the grub menu but it would appear grub cannot recognise my partition as it lists the type as 0x7. What does that mean?

---

### Post by bodhi.zazen on 2007-02-26
You need to use the super grub disk to restore (re-install) grub to your MBR.

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

