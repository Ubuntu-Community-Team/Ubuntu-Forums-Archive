---
title: "Stuck at GRUB Command Line"
date: 2015-11-21
forum: General Help
---

### Post by &amp;*@Fth&amp;% on 2015-11-21
I installed BURG, but then found out it didn't work. So then I reinstalled GRUB, but now whenever I boot up I get this: [http://s000.tinyupload.com/index.php?file_id=00121496778639422706](http://s000.tinyupload.com/index.php?file_id=00121496778639422706). What do I do?

---

### Post by oldfred on 2015-11-21
Probably better to just totally uninstall grub and reinstall it  with advanced options in Boot-Repair.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by leunam12 on 2015-11-21
If after boot-repair you get the same results, try playing with the options at BIOS, there are settings such as fast boot and secure boot that will cause this kind of problem.

---

### Post by &amp;*@Fth&amp;% on 2015-11-21
Thanks! I'll post what happens.

---

### Post by &amp;*@Fth&amp;% on 2015-11-21
It worked <3 :)

---

