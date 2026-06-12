---
title: "Script/autolaunch"
date: 2007-05-24
forum: General Help
---

### Post by arfitty on 2007-05-24
To activate my Sierra air card I run these commands:

ross@Clovertop:~$ sudo /sbin/modprobe usbserial vendor=0x1199 product=0x0112
Password:
ross@Clovertop:~$ sudo mknod /dev/ttyusb0 c 188 0
ross@Clovertop:~$ pppd call Provider


Can anyone tell me either (a) to put these in a script  and/or (b) run them at startup?

Thanks

---

