---
title: "grub rescue and paypal reward"
date: 2013-02-14
forum: General Help
---

### Post by rRecupero on 2013-02-14
Had daul booted 7 and Ubuntu 12. I did it. Didn't think I could dual boot but I did. Now I didn't use Linux that much. So I deleted the partitions I installed Ubuntu on and all was good untill my next boot. My computer won't use windows to boot I'm in grub rescue. Help anyone ? :) anyone that helps with my repair will get PayPal donation.

---

### Post by oldfred on 2013-02-14
No paypal required. (you can buy me a beer or coffee next time I am in town :) ).

You can use a Windows RepairCD or flash and use the Windows procedures, or from Ubuntu liveCD or most other Linux repairCDs install a MBR that works just like Windows.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by rRecupero on 2013-02-14
I'll keep you posted  ......

---

### Post by rRecupero on 2013-02-14
Well it worked. I had made a repair disk but did a few different steps and it didn't work but I followed your steps on windows 7 and the command prompts and in about 3 mins I had windows running.  Anyone else reading this and has a black screen after password verified its recovery doing its thing be patient.

---

