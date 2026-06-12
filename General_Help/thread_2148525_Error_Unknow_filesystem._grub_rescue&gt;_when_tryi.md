---
title: "Error Unknow filesystem. grub rescue&gt; when trying to boot windows 7"
date: 2013-05-25
forum: General Help
---

### Post by koru7 on 2013-05-25
Hello, I recently installed ubuntu 12.04 in a dual-boot with windows 7. I then accidentally deleted the ubuntu partition.  My laptop worked fine until I rebooted and installed windows updates, when i turned my laptop on, grub said:
error: unkown filesystem.
grub rescue>
I know cannot access windows 7.
My laptop is a lenovo thinkpad e530 
Id like to know if i could boot OSX Lion or ubuntu from a usb and use a new bootloader or repair it with ubuntu.

---

### Post by fantab on 2013-05-25
Grub will have most of its boot files in the Ubuntu partition. If you've deleted it (accident or no accident) Grub will not boot anything. When you installed GRUB it overwrote windows boot-loader files on the HDD-MBR. 

What can you do? Either reinstall Ubuntu or Fix Windows 7 MBR with the 'repair disk' or try system recovery. You cannot use Live Ubuntu to fix Windows Boot.

---

