---
title: "Error 15, file not found"
date: 2008-06-04
forum: General Help
---

### Post by kimmme on 2008-06-04
Hello Folks,

I have a booting problems at my Wubi Ubuntu Installation.
As in the Threadtitle the Problem is "Error 15, file not found".

I already tried to solve that problem described [here]("https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742"), but the methods didn't work for me.
The method "Do you have multiple hard disks?"
> If the boot problem happens after the Ubuntu installation (after second reboot) and you have multiple disks, sometimes the disk order at boot is wrong (it is a known bug: [WWW] [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497)). In such cases, edit c:\ubuntu\disks\boot\grub\menu.lst. You have to change all the lines "root (hdX,Y)/ubuntu/disks" to "root ()/ubuntu/disks". Also edit the line that starts with "#groot=(hdX,Y)/ubuntu/disks" to "#groot=()/ubuntu/disks".
didn't work for me because I can't access "c:\ubuntu\disks\boot\grub\menu.lst" out of my Windows System (Path not found).

**Is there any way to get my Wubi Ubuntu Installation running again or at least to get any access from my Windows Intallation for backing up my files** (There are important files stored on that virtual partition)**?**

Thank you!

---

### Post by ago on 2008-06-04
Well the C: in c:\ubuntu\disks\boot\grub\menu.lst is supposed to be changed with whatever drive letter you installed wubi into.

---

