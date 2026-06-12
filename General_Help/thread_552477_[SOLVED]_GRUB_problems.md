---
title: "[SOLVED] GRUB problems"
date: 2007-09-16
forum: General Help
---

### Post by uroskriznar on 2007-09-16
I have WINDOWS installed on harddisk #1 and Ubuntu on harddisk #2. I want to take the first harddisk out of my PC, and only use Ubuntu on harddisk #2. I tired this, but Ubuntu does not boot. I know I have to change some settings in GRUB, but I don't know what. Could someone please help me?

---

### Post by forestpixie on 2007-09-16
this might help you - [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

grub would have replaced the win mbr (i think) - when you've taken the hardrive out, the mbr went too

---

### Post by Irony on 2007-09-16
From a live CD do;

To install grub to the MBR (hda) and point it to a menu.lst in hda3 do;

[PHP]sudo grub[/PHP]

This opens up the grub program, with a prompt of grub>, now type. 

[PHP]find /boot/grub/stage1
root (hd0,2)
setup (hd0)
quit[/PHP]

Here is an example;

[PHP]grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,5)
 (hd0,6)
 (hd0,8)
 (hd0,11)
 (hd1,1)
 (hd1,2)

grub> root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

grub> quit[/PHP]

---

### Post by uroskriznar on 2007-09-19
Thanks guys. I solved the problem. Where do you mark the thread as solved???

---

### Post by forestpixie on 2007-09-19
thread tools at the top near the first post - glad you're sorted

---

