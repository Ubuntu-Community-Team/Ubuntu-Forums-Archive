---
title: "uefi does not show  anything"
date: 2013-08-04
forum: General Help
---

### Post by ihsankocak on 2013-08-04
I have a dell inspiron 15r.Installed on Ubuntu 13.04 64 bit.I was trying to repair my ubuntu via harddisc boot(iso file)(added a menu item to grub2).Ubuntu booted from iso file.I chose "erase ubuntu and reinstall".Then it said something like this:device ... is mounted.unmount the device.Then i tried to umount but it said:device is busy.Then i forced to unmount with ```
umount -f -a /
```.Then when i restarted th pc, there is nothing in uefi booting menu.before that there was an ubuntu choice in uefi booting menu.So i can not drop into a terminal or linux console.i can not do anything to solve this problem.Can you help me?

---

### Post by oldfred on 2013-08-05
The grub menu is in / (root), so if you erased /, you do not have a grub menu. But I thought UEFI kept entries and you had to manually delete them.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

