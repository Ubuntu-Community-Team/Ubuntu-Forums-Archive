---
title: "Deleted GRUB, cant load windows 7"
date: 2015-06-14
forum: General Help
---

### Post by james145 on 2015-06-14
So, not very recentley i decided to delete the 300gb partion that Ubuntu took up from my pc, and being the tard that I am, I now cant boot Windows because Ubuntu got delted. I tried to use the Windows install disk, to get into promp and using one of the commands from another thread, i tried to restore it (/fixmbr) but that didnt work. Plz help, I really hate Ubuntu and I want rid of it!

---

### Post by ventrical on 2015-06-14
> **james145 said:**
> So, not very recentley i decided to delete the 300gb partion that Ubuntu took up from my pc, and being the tard that I am, I now cant boot Windows because Ubuntu got delted. I tried to use the Windows install disk, to get into promp and using one of the commands from another thread, i tried to restore it (/fixmbr) but that didnt work. Plz help, I really hate Ubuntu and I want rid of it!

You may have to download the Grub Rescue kit . It is  an ISO image that can be burned to a CD and it has rarely failed me in problems with restoring Windows 7 boot loader.

Regards..

---

### Post by james145 on 2015-06-14
Do you know where I can aquire this kit? Im quite new to messing about with Os so I have really no clue what I am doing

---

### Post by ventrical on 2015-06-14
> **james145 said:**
> Do you know where I can aquire this kit? Im quite new to messing about with Os so I have really no clue what I am doing

Just do a google search for 'grub rescue download'. Hopefully you will get a reputable site. If you are using Windows you can also download Imageburn and make a bootable grub recovery CD. I advise against Super Grub Rescue.

Regards..

---

### Post by oldfred on 2015-06-15
Boot-Repair or your Linux live installer can restore a Windows boot loader to the MBR if a BIOS system. You also need boot flag on Windows boot partition.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

