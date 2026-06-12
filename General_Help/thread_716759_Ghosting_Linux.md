---
title: "Ghosting Linux"
date: 2008-03-06
forum: General Help
---

### Post by Ingla on 2008-03-06
Hello.

I generally (on Windows) have two identical hard drives in removable drawers in the machine. One is a ghost of the other.

I would like to do this with Ubuntu but, even if I can get some software to ghost my disk (the only thing I know of is G4U), there appears to be a problem.

If the ghosted disk is an exact copy, it probably won't be bootable from a second IDE (or SATA) connection in the motherboard. I will presumable get something like "can't find hda2", or whatever.

Is there any way to fix this?

Any advice appreciated.

Thanks.

---

### Post by frankos44 on 2008-03-06
To get an exact copy, assuming both drives are the same size

unmout the second drive

$sudo dd if=/dev/xxx of=/dev/yyy

where xxx=source drive and yyy=dest drive

use fdisk -l to find out the what xxx and yyy is.

It is slow but does give you an exact copy. 

BE CAREFUL NOT TO MIX IT UP

---

### Post by milton1 on 2008-03-06
you could use gparted to ghost the drive. It is a simple "copy and paste" interface. If the drives are both set as cable select, and you remember to set the "boot" flag after cloning, the second drive will show as hdb, etc, and will be bootable. You can add a grub entry to /boot/grub/menu.list to boot from the backup drive.

---

### Post by Ingla on 2008-03-06
Thanks for the replies.

frankos44:

1. What if the target drive is larger?
2. Will the "cloned" drive be bootable where it is, or will it only work in the same motherboard connection as the original, i.e. would I have to physically move it to boot it?

milton1:

1. What if the drives are not cable select (I usually use "master"), or as with newer disks, there are no jumper options?
2. How do you set the "boot" flag??
3. What would  an entry to /boot/grub/menu.list look like? (As I sometimes have three disks in the machine, I usually reboot and enter CMOS to change the 1st boot device to the one I want ... I assume you're talking about a "menu" item that would give me a choice of either disk at boot?)

Thanks a lot!

---

### Post by frankos44 on 2008-03-07
> **Ingla said:**
> Thanks for the replies.

frankos44:

1. What if the target drive is larger?
2. Will the "cloned" drive be bootable where it is, or will it only work in the same motherboard connection as the original, i.e. would I have to physically move it to boot it?

Thanks a lot!

Yes the cloned drive will be bootable. I am pretty sure that the partition sizes will remain the same. You can of course resize them afterwards using another utility.  Also you can save to an image file on another hard disk too, but in this situation you will need to backup the MBR.

Take a look at [http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)

---

### Post by milton1 on 2008-03-07
> **Ingla said:**
> 
1. What if the drives are not cable select (I usually use "master"), or as with newer disks, there are no jumper options?
2. How do you set the "boot" flag??
3. What would  an entry to /boot/grub/menu.list look like? (As I sometimes have three disks in the machine, I usually reboot and enter CMOS to change the 1st boot device to the one I want ... I assume you're talking about a "menu" item that would give me a choice of either disk at boot?)

Thanks a lot!

1. as long as they are set to both be recognized, you should have no problem. So either both cable select, or one master one slave, or different cables. Your system will still recognize them as distinct drives.

2. In gparted there is an option for "manage flags". you need only check the box next to "boot".

3. Open /boot/grub/menu.list and look at them yourself. Each boot option has its own set of parameters. If you copy the default option and change the drive designation to match your backup drive, it will create a new option to boot to the new drive.

---

### Post by Ingla on 2008-03-12
Thanks.

_**frankos44**_: One thing we forgot to mention. I'm assuming I first need to set up the target hard disk by making partitions that match those on the source disk, i.e. currently, my / partition is hda1 and the home partition is hda5.

I assume I need to run  $sudo dd if=/dev/hda1 of=/dev/hdd1 (or whatever it turns out to be)

and then run $sudo dd if=/dev/hd5 of=/dev/hdd5 (or whatever).

_**OR**_

> I am pretty sure that the partition sizes will remain the same.

Did you mean that this procedure would somehow recreate the partitioning as well?

_**milton1:**_ Same question. If this is > a simple "copy and paste" I guess I have to be pasting to previously created partitions or I'll wind up with everything on just one. Is that correct?

---

### Post by frankos44 on 2008-03-13
> **Ingla said:**
> Thanks.

_**frankos44**_: One thing we forgot to mention. I'm assuming I first need to set up the target hard disk by making partitions that match those on the source disk, i.e. currently, my / partition is hda1 and the home partition is hda5.

I assume I need to run  $sudo dd if=/dev/hda1 of=/dev/hdd1 (or whatever it turns out to be)

and then run $sudo dd if=/dev/hd5 of=/dev/hdd5 (or whatever).

_**OR**_



Did you mean that this procedure would somehow recreate the partitioning as well?

_**milton1:**_ Same question. If this is  I guess I have to be pasting to previously created partitions or I'll wind up with everything on just one. Is that correct?

If for example the source partitions are hda1 and hda5 and the target partitions are hdb1 and hdb5, I am pretty sure that all you need to do is type is:

$ sudo dd if=/dev/hda of=/dev/hdb

There is no need to create the partitions first. The whole drive is mirrored including boot partition, however it is best to boot from another media such as the CDROM first as /dev/hda can change if booted.

This method is only good for cloning and even then you may as well backup your files and then re-install the OS for what it takes. I certainly would not rely on this method for backups because you only have one backup unless you have lots of hard disks, secondly it is very slow.

If backing up your system is the issue, there are many types of backup schemes to put into place. I suggest backing up to more than one type of media and physically keeping a backup elsewhere. This applies to any OS where data is mission critical. 

I use tar for daily backups which are stored locally and on an external hard drive plus monthly backups on a CD. The CD backup does not contain music files, in my case it wont be the end of the world in the rare event that my hard drive packed up and the backup drive packed up at the same time.

---

