---
title: "Grub?"
date: 2004-10-30
forum: General Help
---

### Post by Mosquito on 2004-10-30
My system, hda Windows Me, hdb Ubuntu.

When i installed Ubuntu i Choosed the easy way and just let  it do all the work.
I think Ubuntu installed Grub in mbr on hda.
I share this computer with someone and now I will remove Ubuntu (dont worry I will install it on a different machine).

So the question is how will it affect my hda disc if I uninstall Ubuntu from hdb?

Mosquito....

---

### Post by triad169 on 2004-10-30
A little tough to answer your question because dont know what other operating systems you are running.  But if

hda = windows xp
hdb = ubuntu

You system will boot up and Grub will give you and error message because the the config files needed by grub (located in /boot under Ubuntu install)  will be gone.   You will need to boot your system from your Windows XP cdrom and enter recovery console.  Then fix the master boot record so when computer boots windows will load.  You can get some info on this at:

[http://www.microsoft.com/windowsxp/home/using/productdoc/en/bootcons_fixmbr.asp](http://www.microsoft.com/windowsxp/home/using/productdoc/en/bootcons_fixmbr.asp)

Triad

---

### Post by Mosquito on 2004-10-30
My system:

hda windows me
hdb Ubuntu

---

### Post by phoolgobi on 2004-10-30
i dont know how to do this from linux but this is what i have done in the past when i wanted to remove a linux installation...

1. download ranish partition manager (a couple of hundred kb)
2. boot machine in dos mode with a windows bootable cd/floppy
3. start partition manager
4. select mbr entry of required disk
5. change type to standard
6. save changes
7. press F5 to select other disk. u can now change partiotion type from ext2/3/swp/... to FAT16/32/...

this will replace grub in mbr of ur hda, to a standard windows loader

works with all versions of windows

hope this helps...

---

### Post by Joeb on 2004-10-30
Couldn't you just boot to the Windows Me partition and run fdisk /mbr to replace the boot loader?  That won't remove the linux partition on hdb, but it can be left alone until ready to install something else.

---

### Post by Mosquito on 2004-10-30
"Some dual-boot programs have a special MBR that asks you at startup which operating system you want to use. The fdisk /mbr command erases this program. Dual-boot systems that boot whichever partition is marked Active are not affected by the fdisk /mbr command".

Ubuntu starts by default if I don´t press Esc at boot, then I can choose wich Os to start.

So does that mean Grub is the second type (Ubuntu as active)?

---

### Post by FLeiXiuS on 2004-10-30
To begin this, 

Its very easy to fix the MBR if windows is installed on the primary drive also.

If your dual booting windows/linux then simply delete the linux partition then find a copy of the windows system restore cd.

Boot to the CD then select Recovery Console.

From there type:
```

fixmbr

```

Relatively easy!

---

