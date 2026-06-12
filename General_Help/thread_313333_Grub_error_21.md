---
title: "Grub error 21"
date: 2006-12-05
forum: General Help
---

### Post by qwerty11 on 2006-12-05
I recently installed ubuntu on to an external harddrive and grub on my primary hard drive now whenever i turn on my computer it show the error 21... note i am posting using the live cd. please help

---

### Post by az on 2006-12-05
> **qwerty11 said:**
> I recently installed ubuntu on to an external harddrive and grub on my primary hard drive now whenever i turn on my computer it show the error 21... note i am posting using the live cd. please help

Error 21 means that your bios cannot find the place where Ubuntu is installed.

Before your OS loads, it's your BIOS that tells your bootloader where to look for the stuff it needs to boot your system.  In this case, your bios is either buggy or just plain incapable of locating the USB drive and booting from it.

---

### Post by qwerty11 on 2006-12-05
> **azz said:**
> Error 21 means that your bios cannot find the place where Ubuntu is installed.

Before your OS loads, it's your BIOS that tells your bootloader where to look for the stuff it needs to boot your system.  In this case, your bios is either buggy or just plain incapable of locating the USB drive and booting from it.

how do i make it so i can load windows again. i dont have my windows cd >.<

---

### Post by kevinlyfellow on 2006-12-06
You can try reinstalling grub, or one thing that works well is creating a grub boot floppy using puppy linux (puppyos.com).  

For reinstalling grub, try [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

For making a boot floppy using puppy linux
there is a script somewhere in the menus... I can't think of it right now... but look around and explore.

---

### Post by az on 2006-12-06
> **qwerty11 said:**
> how do i make it so i can load windows again. i dont have my windows cd >.<

Well, it's complicated.  The easiest was would have been for you to restore your MBR so that the first OS on the disk boots.  You would need a windows disk to fix the MBR.

I dunno if you can just zero out the MBR, or run

fdisk /mbr

You can also use the Ubuntu disk to boot the first OS on the first hard disk (I think).

The complicated fix is to make a small /boot partition on your disk and grub will install itself there.

---

