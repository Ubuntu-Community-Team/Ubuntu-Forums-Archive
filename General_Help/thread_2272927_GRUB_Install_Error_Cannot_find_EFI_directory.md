---
title: "GRUB Install Error: Cannot find EFI directory"
date: 2015-04-09
forum: General Help
---

### Post by Kpenguin on 2015-04-09
Hi everyone,
I have a dual boot, 64 bit laptop with Windows 8 on one partition and Ubuntu 14.04 on the other. Windows recently updated and now GNU GRUB no longer appears when I boot my computer. I found information on the following website on how to repair it:[ http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd")
This worked fine until I got to this command:```
grub-install /dev/sda
```
When I put this command into terminal, it says: ```
grub-install: error: cannot find efi directory
```
I found information about this error on the following website: [https://bbs.archlinux.org/viewtopic.php?id=178423](https://bbs.archlinux.org/viewtopic.php?id=178423)
There are two commands suggested on that site, one does not work at all, the other gives me the error ```
/boot/efi does not appear to be the efi partition
``` or something like that.
Could someone please help me get GRUB back so I can use Ubuntu again please?
Thanks in advance.

---

### Post by oldfred on 2015-04-09
Your link is to the full chroot (CHange ROOT) to use the kernel from live installer, but be working in your system. But it is a bit older for BIOS based systems. You also have to mount the efi partition and any other system partitions that some have as separate partitions. You should just need to add a mount of the efi partition.

Usually most desktops do not have separate partitions for other system folders, a few do have separate /boot but that is not recommended for most desktops. 

 UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

But often easier to use Boot-Repair.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by yancek on 2015-04-09
Use the Ubuntu installation CD/flash drive (or any Linux) and go to the boot repair site, download and run it selecting the option to Create Boot Info Summary.  Post the output text file here as it will have more detailed information on your system(s).

---

### Post by Kpenguin on 2015-04-09
Hi,
I tried the boot repair application and it worked great! I now have GRUB and Ubuntu back.This is rather minor, but I now also have a bunch of other stuff that wasn't there before (see attached screenshot).
[ATTACH=CONFIG]261200[/ATTACH]
I previously just had Ubuntu, Advanced options for Ubuntu, Windows boot manager, and System setup. Is there some way to get rid of the stuff in between?
Again, this is minor and not vital :)
Thanks for your help!

---

### Post by oldfred on 2015-04-09
HP seems to have a lot of its recovery/repair files as efi files in the standard efi(ESP) partition. So Boot-Repair just adds them to the grub menu.
Boot-Repair normally creates a new 25_custom folder. That is just from Boot-Repair so you can edit at will.

       Just to have a backup.
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
Edit :
gksudo gedit /etc/grub.d/25_custom
Or:
sudo nano /etc/grub.d/25_custom
Then do:
sudo update-grub

---

### Post by Kpenguin on 2015-04-10
So, I need to follow those steps and then re-run boot manager, or just update GRUB?

---

### Post by oldfred on 2015-04-10
Just the steps shown.
Boot-Repair would probably add them back again. :)

---

### Post by Kpenguin on 2015-04-10
Wow.... That was easy. :) Thanks for your help!

---

