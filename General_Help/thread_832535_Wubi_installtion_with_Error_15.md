---
title: "Wubi installtion with Error 15"
date: 2008-06-17
forum: General Help
---

### Post by Kejing on 2008-06-17
Yesterday, I install Ubuntu via Wubi under Windows XP SP3 En version.  The Ubuntu was installed on a removal USB disk

When wubi asked me to reboot the system, then I followed the instruction. Then the system stuck with the following information

```

find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

Error 15: File not found
Press any key to continue... 


```

After pressing enter, I got another message

```

GRUBDOS 0.4.3 2008-4-22 Memory: 639k/1014M, CodeEnd: 0x41228

find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst
commandline
reoboot
halt 

```

What am I supposed to do?

---

### Post by tinybit on 2008-06-17
press c to enter command line, at the grub prompt type these commands:

```

debug on
geometry (hd0)
geometry (hd1)
geometry (fd0)

```

This should list your partitions and filesystems in your machine.

If it can not list anything for your USB drive, then you may try to install a grub4dos with the build grub4dos-0.4.3-2008-06-12-geometry-tune-test-only.zip found at [http://grub4dos.jot.com/](http://grub4dos.jot.com/)

---

### Post by ago on 2008-06-18
[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

---

