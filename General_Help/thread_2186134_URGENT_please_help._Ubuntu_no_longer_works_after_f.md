---
title: "URGENT please help. Ubuntu no longer works after formatting"
date: 2013-11-05
forum: General Help
---

### Post by blairbolema on 2013-11-05
I accidentally formatted my local disk(D)on win8 which only contained some kind of shortcut. Now when I try to boot up ubuntu i get sent to a grub menu i've never seen before. It says [CENTER]                             >                          GNU Grub version 1.99-21ubuntu3.10 
Minimal BASH-like line editing is supported. For the first word ,TAB lists possible command comletions. Anywhere else TAB lists possible device or file completion[/CENTER]
> 

After which i am not able to do anything besides hit TAB. When i type boot it says that there's no loaded kernel. 
Does anyone know what to do about this? I am/was running Ubuntu 12.04

---

### Post by Impavidus on 2013-11-06
I wonder what Windows has been doing...
Run [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) from a live disk and post the link to the summary it gives you. Don't run any repair, just generate the summary.

---

### Post by grahammechanical on 2013-11-06
My guess would be that what Windows calls disk D was in fact the partition that Ubuntu was installed on. Windows does not read Linux disk/partiton formats so the some kind of shortcut that you refer to may have been Windows inability to read the partition format of the Ubuntu partition. Grub is giving you a Grub command line because it cannot find the files it needs to load Ubuntu. You may need to re-install.

---

### Post by oldos2er on 2013-11-06
If you have an Ubuntu LiveDVD or LiveUSB, can you boot from it and run the bootinfo script? [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by blairbolema on 2013-11-06
I will try to download boot repair but currently my internet is very spotty and may take a few days. If i instead reinstall ubuntu from a live CD would that erase the data in that partion?

---

### Post by Impavidus on 2013-11-06
Not necessarily, you can reuse the partition without formatting, which will keep your files. You can use the live disk to copy files to an external disk too.

The question however is whether the partition is still there, as this grub error often indicates the partition is gone. If it's not there, you may have success with [filesystem recovery](https://help.ubuntu.com/community/DataRecovery) (see under "Lost Partition") or (if this doesn't work) use the backups I hope you have and start from scratch.

You may also be lucky, it might be a grub update gone wrong (happened once to me), but that would be an unlikely coincidence.

---

