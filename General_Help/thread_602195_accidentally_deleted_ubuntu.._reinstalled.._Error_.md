---
title: "accidentally deleted ubuntu.. reinstalled.. Error 13 cant mount?"
date: 2007-11-04
forum: General Help
---

### Post by DB6150 on 2007-11-04
I accedentally removed 7.10 when trying to resize the partition so i could use part of the hdd for windows backups.

so of core the boot settings where lost. i reinstalled 7.10 and now when i try to load it gives a error 13 cannot mount .... 

any ideas how to fix this? 

im running off the live cd at the moment

---

### Post by dcstar on 2007-11-04
> **DB6150 said:**
> I accedentally removed 7.10 when trying to resize the partition so i could use part of the hdd for windows backups.

so of core the boot settings where lost. i reinstalled 7.10 and now when i try to load it gives a error 13 cannot mount .... 

any ideas how to fix this? 

im running off the live cd at the moment

I am assuming that the problem is with Grub (you have not specified nearly enough information for anyone to really help you), so what may have happened is that the UUID in the /boot/grub/menu.list file may now be incorrect.

If so, then you need to - using the Live CD - mount the new Linux partition on the hard disk, and edit that file replacing the UUID info with the basic /dev/hdx (or /dev/sdx) designation.

---

### Post by DB6150 on 2007-11-04
> **dcstar said:**
> I am assuming that the problem is with Grub (you have not specified nearly enough information for anyone to really help you), so what may have happened is that the UUID in the /boot/grub/menu.list file may now be incorrect.

If so, then you need to - using the Live CD - mount the new Linux partition on the hard disk, and edit that file replacing the UUID info with the basic /dev/hdx (or /dev/sdx) designation. 

yes the problem is with grub... i know very little of ubuntu and i do not know how to do what you said.. if you can , please put it in simplier terms. 

and if you need anymore information tell me and ill try to get it  


thanks for the help thus far

---

### Post by dcstar on 2007-11-04
> **DB6150 said:**
> yes the problem is with grub... i know very little of ubuntu and i do not know how to do what you said.. if you can , please put it in simplier terms. 

and if you need anymore information tell me and ill try to get it  


thanks for the help thus far

Look here, it seems a very similar problem to yours:

[http://ubuntuforums.org/showthread.php?t=594399&highlight=mount+live+cd](http://ubuntuforums.org/showthread.php?t=594399&highlight=mount+live+cd)

---

### Post by DB6150 on 2007-11-04
well i tried the thign son there and i can get into the menu.lst ... but i cannot find out how to mount it to the hard drive

---

### Post by DB6150 on 2007-11-04
i put 7.04 in 7.10's place and booted into windows by using the live cd option im now going to completly delete and format the linux partitions to NTFS... which will get me back to phase one where i can hopefully mount the drive like normal in the install setup

---

### Post by DB6150 on 2007-11-04
Ok got it all working and a 40Gb hdd on order for linux and linux only :)

---

