---
title: "Grub (v1.99) fails to load Windows 7 after upgrade to Ubuntu 14.04.1 LTS"
date: 2014-11-09
forum: General Help
---

### Post by jacob.david on 2014-11-09
I have the following setup. This used to work with Ubuntu 12.04.1 LTS without any problem. But after the update grub fails to load windows and I can't figure out why. 
sda --> Windows
sdb --> Ubuntu 14.04.1 LTS. Grub is installed here.
I have attached the boot info script.
Thanks in advance for any help, much appreciated.

---

### Post by yancek on 2014-11-09
Your bootinfoscript shows you are using Dynamic volume (as indicated by SFS under the System column in the fdisk output for the windows on sda.  I don't believe you will be able to boot windows from Grub because of this, at least from what I have read about it.  You do have windows in the master boot record of sda so you should be able to select that drive in the BIOS or boot options on boot.  The link below has some information on this which may be helpful.

[http://ubuntuforums.org/showthread.php?t=1653493](http://ubuntuforums.org/showthread.php?t=1653493)

---

### Post by jacob.david on 2014-11-14
Thanks for the reply and apologies for the delay in getting back to you. Yeah I currently boot windows/Linux by tweaking the BIOD setting which is bit of a hassle. The dual boot used to work with the previous Ubuntu LTS. And windows hasn't been changed at all. I will go through the link and see whether I can find anything useful for me.

---

