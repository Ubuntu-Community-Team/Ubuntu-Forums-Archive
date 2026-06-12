---
title: "Grub error 25 after adding cdrom"
date: 2006-10-22
forum: General Help
---

### Post by dbendlin on 2006-10-22
Hello guys, I have a grub 25 error after adding a cdrom, this is my conf:
/dev/hda 40GB IDE Containing a NTFS partition and windows installation
/dev/hdb 40GB IDE Containing a NTFS partition
/dev/hdc 80GB IDE Containing (Ubuntu installation)

This works fine and i configured grub to be able to boot my Win XP OS. After adding a cdrom /dev/hdd and booting I get the grub error 25. Any clues on how to fix this?

Thanks in advance for your help and support,

Kind regards,

Diego Bendlin

---

### Post by Kateikyoushi on 2006-10-22
> 25 : Disk read error 
This error is returned if there is a disk read error when trying to probe or read data from a particular disk.

Are you able to boot if you disconnect the cd ?
How did you install it without cd ?

---

### Post by Herman on 2006-10-22
Hello dbendlin,
I agree with Kateikyoushi,
Grub error 25 has occurred in previous cases after someone has unplugged their hard disk drives and then plugged them in again differently. 
Refer to this link, [Grub Error 25]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25")

_ If you are sure you didn't make any mistakes with the way all your disks are plugged in_, you might be able to reconfigure Grub to work around the issue, you would possibly be able to use Command Line Grub for doing that with, read the following link, it will explain how, Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

If you can't get a Grub Command Line Interface from you hard disk, but your new CD drive will work okay, you can use a [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"), either in text mode, or press 'c' for the grub command line. [Documentation for Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html").

Regards, Herman :D

---

### Post by dbendlin on 2006-10-22
Thank you guys,

I installed with the CD, but after instalation I needed to disconect my cdrom to use it in another box, after reconnecting it (Exactly the same way as in installation time) i got the error 25. 

If I disconnect the cdrom im able to boot allright.

I'll read the links above and let you know ;)

---

### Post by Kateikyoushi on 2006-10-22
Is the master, slave setting on the drives the same ?
Can you show the output of this command if you boot from live cd ?

```
sudo fdisk -l
```

---

### Post by dbendlin on 2006-10-22
Yes, the bios actually shows disk the same way as before and during installation:

Primary Master (HDD 40GB)
Primary Slave (HDD 40GB)
Secondary Master (HDD 80GB)
Secondary Slave (CDROM)

Does /etc/fstab can have something to do with this error?

Im not near the box with the prob, but i'll try to run fdisk to see how ubuntu is detecting my drives.

---

### Post by Kateikyoushi on 2006-10-22
No it is not your fstab. I think your cd and ubuntu hdd might got switched so when the cd is in the machine grub can not find /boot.

---

### Post by adrian15 on 2006-10-24
1) Your cdrom is not configured ok and althought you think it is an slave... its switches does not reflect this configuration. Then Grub tries to request hard disks file to a cdrom device and gets an error.

 or

2) Or you need to reinstall grub (Super Grub Disk -> Linux -> Fix Linux Boot (Grub)) each time you plug or unplug the cdrom, what you shouldn't need to do. It is weird.

I think that when you plug the cdrom hd0 becomes the cdrom and hd1 becomes the hard disk (and before that hd0 was the hard disk) ... sometimes when reinstalling Grub to the hard disk the hd0 string is hardcoded this make difficult to move the drive (equivalent to connect or disconnect your cdrom).

adrian15

---

