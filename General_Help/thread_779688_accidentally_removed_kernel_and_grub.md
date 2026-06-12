---
title: "accidentally removed kernel and grub"
date: 2008-05-02
forum: General Help
---

### Post by cheeseman557 on 2008-05-02
Hi,

I somehow managed to remove a few old kernels as well as grub from my system. I already tried restoring grub by using setup (hd0) command (found at this link:[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)), but my menu.lst is empty and when I boot, I just get the grub prompt. My boot folder has these files in it:

```
abi-2.6.24-17-generic         initrd.img-2.6.24-17-generic.bak
config-2.6.24-17-generic      memtest86+.bin
grub                          System.map-2.6.24-17-generic
initrd.img-2.6.24-17-generic  vmlinuz-2.6.24-17-generic

```

I'm using the LiveCD now. Thanks for your help!

---

### Post by zdea on 2008-05-03
I manged to do something similar last night, I turned on the Hardy Proposed updates, installed some updates and was prompted about my grub file. It was attempting to update it with the new kernel references to /boot/vmlinuz-2.6.24-17-generic, which I let it do. After a reboot I was dumped to busybox. Then while booting I used grub to edit the line back to my previous kernel: /boot/vmlinuz-2.6.24-16-generic, where necessary and it booted fine. I look in my boot folder and I see I have references to both kernels. I'm thinking a proposed update should be rejected but then again this is my first post and I'm fairly new to ubuntu.

---

### Post by strabes on 2008-05-03
You **have** tried reinstalling grub? The link in my signature should help you.

---

### Post by cheeseman557 on 2008-05-03
I got it fixed, but those links dont work. I had to manaually write a few lines of code in the grub prompt (load the kernel/initd) before booting booting back up.

---

