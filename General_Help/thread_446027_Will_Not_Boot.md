---
title: "Will Not Boot"
date: 2007-05-16
forum: General Help
---

### Post by davethewave83 on 2007-05-16
I instlled Wubi on my IBM 240x Thinkpad but the only OS that will boot is WINXP, when I select Ubuntu it just says something about grub starting.. yadda yadda then the screen goes black and it restarts itself. What would cause this? Thanks!

---

### Post by ago on 2007-05-16
Can you give us a more detail error report?

---

### Post by davethewave83 on 2007-05-16
not really, after the line thats "Kernel /wubi/boot/linux/ find=/wubi/boot/linux quiet ro"
and under that is  [linux-bzimage, setup=0x1c00, size=0x1a82cc] then it just goes to a black screen and reboots. :confused:

---

### Post by davethewave83 on 2007-05-16
forget it, I'll just keep winblows alone I guess. :(

---

### Post by ago on 2007-05-17
You may want to try to defrag the wubi folder and make sure it is not compressed. You can use contig or jkdefrag for that (both free).

---

### Post by tinybit on 2007-05-17
> **davethewave83 said:**
> not really, after the line thats "Kernel /wubi/boot/linux/ find=/wubi/boot/linux quiet ro"
and under that is  [linux-bzimage, setup=0x1c00, size=0x1a82cc] then it just goes to a black screen and reboots. :confused:

Let me see. Too large an INITRD? Or INITRD loading in memory conflicts with VIDEO or other memory used by BIOS(i.e., system memory)?

---

