---
title: "how to load solaris 11 into lubuntu 12 grub bootloader"
date: 2014-03-06
forum: General Help
---

### Post by i57chevy on 2014-03-06
I've installed lubuntu 12.04 on one partition, and solaris 11 on another partition.  I've edited 40_custom and sudo update-grub and still no solaris menu at boot.

please help!
need solaris for school labs

---

### Post by oldfred on 2014-03-08
Someone posted this, but it must depend on where Solaris is installed. It must have a boot loader in the partition it is installed into. Example below hd1,2 is second drive, second partition.

 [http://ubuntuforums.org/showthread.php?t=1529658](http://ubuntuforums.org/showthread.php?t=1529658)
menuentry "OpenSolaris 2010.03 snv_134 64bit" {
    set root='(hd1,2)'
    chainloader +1
}

---

