---
title: "grub rescue problem"
date: 2013-02-02
forum: General Help
---

### Post by Own3r4ever on 2013-02-02
hello.. i had ubuntu installed along with vista and then i removed the partition of ubuntu.. then comes up the grub rescue thing and i cant do anything.. and all i want is to get back to vista and remove all kinds of things that have to do with ubuntu.. this is an acer laptop and everything that has to do with recovery is on the hard-disk and i cant seem to open up the erecovery management with alt + f10 when the laptop boots to restore to factory settings or repair the startup.. 

PLEASE HELP. thanks.

---

### Post by gavinjb on 2013-02-02
I had this problem several years ago and I had to use a recovery CD/Windows CD.

From what I remember you have to run a command to re-install the Windows Boot Loader, if you try something like the link below it should get you up and running again.

[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/]("http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/")

---

### Post by oldfred on 2013-02-02
If you have the Vista RepairCD then gavinjb's link is good.

If you do not have a Vista repairCD you can use Ubuntu.

       An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

    
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
From an Ubuntu liveCd
       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

    
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

