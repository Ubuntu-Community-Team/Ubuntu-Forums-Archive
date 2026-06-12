---
title: "Unable to load windows 7"
date: 2013-02-15
forum: General Help
---

### Post by froggyjump on 2013-02-15
Hello

I had an Acer laptop that had Ubuntu and Windows 7 on it. I wanted to get rid of Ubuntu so I went into disk management and deleted the volume in the partition in which Ubuntu was placed. After doing this I continued to use the computer for a bit longer and then turned it off. Upon returning and turning the computer back on I arrived at a black screen that said

error: unknown filesystem
grub rescue>

I have no idea what to do or what happened. I had 5 partitions created and all I did was delete the volume from one of them. I am extremely confused on what to do and I need to be able to open Windows back up. 

I have already tried the command:

ls (hd0,msdos1/2/3/5) 

I have tried that command with those 4 numbers switched in and I got the response unknown filesystem every time. Could someone please help me, I am extremely lost and confused on what to do.

---

### Post by carl4926 on 2013-02-15
You need the windows dvd to fix the windows bootloader.

---

### Post by oldfred on 2013-02-15
You just need a Windows boot loader in the MBR. Grub in the MBR is looking for the rest of grub including grub menu in the partition you deleted.

You can use a Windows repairCD to run auto repairs 3 times (yes 3x) or manually the fixMBR command.

Or you can use Ubuntu liveCD and install a boot loader that will boot Windows.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)


       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

