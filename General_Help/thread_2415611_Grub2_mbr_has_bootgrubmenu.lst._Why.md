---
title: "Grub2 mbr has /boot/grub/menu.lst. Why?"
date: 2019-03-28
forum: General Help
---

### Post by sampsonats on 2019-03-28
[http://paste.ubuntu.com/p/WH88Kjj6w4/](http://paste.ubuntu.com/p/WH88Kjj6w4/)


[LIST=1]
[*]Any idea why this Grub2 mbr system has a menu.lst file on it?  Did I maybe have an old tool that installed legacy grub somewhere along the way?
[*]Does menu.lst have any effect since I'm using grub2?
[*]Can I safely delete the menu.lst file?
[/LIST]

Thanks!

```
 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No known boot loader is installed in the MBR of /dev/sdc.


sda1: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sda2: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.2 LTS
    Boot files:        **[COLOR=#ff8c00]/boot/grub/menu.lst[/COLOR]** /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img /boot/grub/i386-pc/core.img



```

---

### Post by Rubi1200 on 2019-03-30
Hi,

Did you previously have other Linux distros or Windows installed on your partitions?

If yes, then the menu.lst would have contained that information.

No need to delete in my opinion.

Thanks.

---

### Post by yancek on 2019-03-31
Ubuntu has been using Grub2 for almost ten years so it would have to be a very old computer or some other OS.  Should not be a problems deleting it but moving it to another location first then test re-booting might be safer.  Not much point in deleting it as it is a tiny file.

---

### Post by sampsonats on 2019-03-31
I’ve been using this machine to practice on. I have lots of machines at customer’s sites running Ubuntu 12.04 that I need to update to Ubuntu 18.04. I have to do the updates remotely with no physical presence at the target machines. The target machines all are using grub2. They have only the 12.04 OS on sdb and they have a sda data drive. BIOS points to sda. I think when it tries to boot from sda, grub on sda runs but since there is no OS there it falls back to BIOS and finally boots from sdb. 

Kind of strange, but that’s what’s out in the field so I have to work with it. The reason I asked the question about menu.lst is just for my understanding. I thought menu.lst was the config file for grub1. I suspect that I mistakenly got hold of an old boot repair tool from the grub1 days. I think what I need to confirm is that menu.lst is not used for grub2. 

Thanks.

---

### Post by sampsonats on 2019-03-31
I guess I lied a little. I described my target machines. My practice machine started out like my target machines but now has a rescue OS on sda. That’s where the menu.lst file is. The rescue OS is Ubuntu server 18.04 so not sure where menu.lst came from.

---

### Post by yancek on 2019-03-31
> I have lots of machines at customer’s sites running Ubuntu 12.04 that I need to update to Ubuntu 18.04

Your a little behind the curve as support for 12.04 ended 2 years ago so I believe you will need to first go to 16.04 then 18.04.  

> I thought menu.lst was the config file for grub1

That is correct although some distributions used a file named grub.conf rather than menu.lst, same function.  The last Ubuntu which used Grub Legacy was 9.04 so that's almost 10 years?

There is absolutely no reason why a person cannot have Grub code in the MBR of one physical hard drive pointing to and boot Grub on a second hard drive.  Lots of people do something similar using a flash drive which contains only boot files.  I guess they feel it is safer?

---

