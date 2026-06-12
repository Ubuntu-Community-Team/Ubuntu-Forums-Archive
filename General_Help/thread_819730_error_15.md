---
title: "error 15"
date: 2008-06-05
forum: General Help
---

### Post by hdchump on 2008-06-05
hi guys!

can you please help me get this baby up and running?
edit:
i have had vista installed when using wubi but now only XP and wubi.
same thing has happened in like 10 tries. 
did a clean xp install most recent and got the error 15: file not found. 
then i installed ubuntu on a second partition formatted first with ntfs and selected
manual config for the partition and swap (19 GB and 999 MB).
that install didnt even show up in the bootldr or grub.

HELP!! 

menu.lst

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 3
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

---

### Post by hdchump on 2008-06-06
...guess not

---

### Post by ago on 2008-06-06
[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

---

