---
title: "Grub-Customizer"
date: 2022-10-23
forum: General Help
---

### Post by rambo15 on 2022-10-23
Good Afternoon:
I just installed Ubuntu on my Dell Laptop and I would like to change the grub boot order menu. I tried to install grub-customizer as follows:

Admin@Alpha-Latitude-E5550:~$ sudo apt install grub-customizer
[sudo] password for admin: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package grub-customizer

Much gratitude in advanced for any and all suggestion!

---

### Post by oldfred on 2022-10-23
I prefer to not use grub-customizer.
It replaces grub's scripts with its own proxy files. 
Not sure if it is yet updated for 2.06.

What order do you want to change?
You can use efibootmgr to change UEFI boot order.
Or copy boot stanza's into 40_custom and copy to 06_custom so first in boot order.Or just change entry in /etc/default/grub so different line in grub is default.

Post current order & what you want to change and we can give specific edits to make.
List of grub menu:
cat /boot/grub/grub.cfg  | grep menuentry

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example to another grub.cfg
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

Lots of detail:
[https://www.gnu.org/software/grub/manual/grub/grub.pdf](https://www.gnu.org/software/grub/manual/grub/grub.pdf)

---

