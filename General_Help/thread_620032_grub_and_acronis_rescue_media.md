---
title: "grub and acronis rescue media"
date: 2007-11-22
forum: General Help
---

### Post by hodgestructure on 2007-11-22
( I know this is not a question about ubuntu, but it's related to grub...)

In a cd with gurb, I tried to type the following in the menu.lst:

title acronis
chainloader --force /acronis.bin
boot

But it showed that:

Starting Acronis Loader...
Boot failed, press any key...

Can someone help me with this issue?

I don't want to use the following:

title Acronis True Image
kernel /TI/DAT3.DAT vga=791 ramdisk_size=32768 mbrcrcs=on
initrd /TI/DAT2.DAT /s

I have tried the above, it works , but different from what I have seen
when I boot the pc with the original Acronis Rescue Media.

Thanks....

---

