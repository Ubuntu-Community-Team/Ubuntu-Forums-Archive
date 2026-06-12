---
title: "How to Remove Grub from my Computer!!!???"
date: 2015-06-05
forum: General Help
---

### Post by Krishna_Siva on 2015-06-05
Hi Guys, I just installed Xubuntu on my pc dual booting with win7. Then I wanted to restore my computer to factory state and used my internal windows recovery drive (or /dev/sda1 recovery)  to change in to factory state. It formatted the disk and again installed win7, so Xubuntu gone. now when I boot, it takes me to grub rescue mode. I am now on a makulu linux live cd. I want to remove grub.I dont have a windows recovery cd, and using boot=(hd0), prefix=(hd0)/boot/grub, insmod normal, normal doesn't work for me. what to do?please help!!!

---

### Post by yancek on 2015-06-05
Your attempts to use Grub to boot windows won't work in your situation as you have deleted the partition on which Xubuntu resided.  This is the partition on which almost all Grub files were located.  You should have first changed the boot code in the MBR with windows before deleting Xubuntu.  I'm not sure I understand why if you set to factory defaults with your Recovery partition you are not able to boot or am I misreading your post?  The best way as well as easiest is if you have an actual installation media for windows.  Since you don't, you will have to try other options.  The link below has one possibility, I'm not sure it will work with Makulu as I'm not familiar with it:

[http://askubuntu.com/questions/149674/how-to-create-or-recover-windows-bootloader-after-deleting-ubuntu-boot-drive](http://askubuntu.com/questions/149674/how-to-create-or-recover-windows-bootloader-after-deleting-ubuntu-boot-drive)

Another option explained at a windows 7 forum but requires a windows upgrade disk: 

[https://windowsforum.com/threads/how-to-remove-grub-loader-and-get-windows-7-boot-loader-back-uninstalling-linux.34709/](https://windowsforum.com/threads/how-to-remove-grub-loader-and-get-windows-7-boot-loader-back-uninstalling-linux.34709/)

---

### Post by oldfred on 2015-06-05
I tend to prefer Lilo(bootloader only) or Syslinux as Windows type boot loaders. The mbr one should work but is older.
Boot-Repair restores the syslinux boot loader for Windows.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Windows screenshots:
[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

Lilo is in repository:

 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

---

