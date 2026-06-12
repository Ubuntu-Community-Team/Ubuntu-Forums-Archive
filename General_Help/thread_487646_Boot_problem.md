---
title: "Boot problem"
date: 2007-06-29
forum: General Help
---

### Post by Washington Irving on 2007-06-29
After i installed a fresh version of Feisty I have to keep the CD in the drive to boot up and press "boot from first hard disk" to load Ubuntu (GRUB is then displayed). I don't actually want to boot up Windows because it is broken (this is why I re-installed Ubuntu) but I would like to get my boot up working on its own. If I leave it now it just hangs after it says "boot from CD:"

Help appreciated.

Thanks.

---

### Post by Herman on 2007-06-29
Hello Washington Irving,
Have you gone into your BIOS and checked that the hard disk is listed as one of your deviced to boot in your boot order?
(Sorry if that's an obvious suggestion, but I have to start at the beginning) :D

Also, can you try installing GRUB to MBR? Try this, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") eg; with Live CD.
If you know what to do when you read that link then fine, but if you need more help you should try to send a copy of the output from 'sudo fdisk -lu' so someone can see what your partitions are like so they can help you,
```
sudo fdisk -lu
``` Or post a screencap from Gnome Partition Editor instead if you prefer.
Thanks, 
Regards, Herman :D

---

### Post by Washington Irving on 2007-06-29
I have checked that the hard disk is in the boot order, it is after floppy and CD. I don't really know where to start on the linked page so here is the output from that command:

```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   268414019   134206978+   7  HPFS/NTFS
/dev/sda2       268414020   484166969   107876475   83  Linux
/dev/sda3       484166970   490223474     3028252+   5  Extended
/dev/sda5       484167033   490223474     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by Herman on 2007-06-29
That looks like a normal healthy fdisk output, good. :D

Okay, try these commands, these should install the 'IPL' (Initial Program Loader) for GRUB in your number 2 file system, (partition), to the area in your hard disk's master boot record that is reserved for boot loader code.  This is called GRUB's stage1.
I will also install GRUB's stage1_5 to the next fifteen sectors of the first track of your hard disk. These are normally empty and are mainly used by boot loaders.

Here we go then,
```
sudo grub
```The above command should ask for your password and then give you a grub>_ prompt. That means you're in a grub shell.
```
find /boot/grub/menu.lst
```This command is just a safety check to verify (hd0,1) as the Ubuntu partition. Grub should reply '(hd0,1)' if everything is as expected.
```
root (hd0,0)
```The above command is to focus grub on the partition we want to install grub from. (in case you have other Linux installs in the same computer).
```
setup (hd0)
``` This command sets up your master boot record and the next fifteen sectors with the two grub stages I already mentioned.
Now the MBR will point to GRUB in your Ubuntu partition when you boot your computer up. 
```
quit
``` That closes the GRUB shell
```
exit
``` The 'exit' command closes the terminal.

If you don't like using the command line, you can do the same thing by choosing menus with  [Super Grub Disk]("http://geocities.com/supergrubdisk/"), just download one of those and burn it to a CD-ROM, or make a floppy disk or USB disk from it. (you must choose the appropriate file to download). SUper GRUB Disk is free and it's a very small download. And it's extremely useful. :D

Now you should be able to reboot and you should have a GRUB menu.

If this doesn't work we will need to investigate why not. Maybe you have some kind of antivirus or MBR write-protect feature locking your MBR in your BIOS. [    Turn off MBR antivirus or write protect]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect")
Or maybe you have a problem with the way your hard disk is plugged in and detected in your BIOS. 
Maybe try switching your hard disk to first in your BIOS and see if that helps.

Try what I suggested so far if you like , and see how you go.
Regards, Herman :D

EDIT: I just noticed there is no boot flag showing in your partition table in that fdisk output.  When you install GRUB, it can set its own boot flag automatically with its 'makeactive' command. You can also do that from your GRUB command line or with Super GRUB Disk or with any partition table editing software, such as Gnome Partition Editor in Ubuntu. Maybe that's all your problem is.

---

### Post by Washington Irving on 2007-06-30
Ok, I tried the "makeactive" command first but that returns ```
Error 12: Invalid device requested
``` I then tried the steps which you originally suggested but unexpectedly get "(hd1,1)"

---

### Post by Herman on 2007-06-30
Aha! :D

Your computer seems to be confused about which of your hard disks is the first one and which one is the second hard disk.
Normally when IDE and SCSI (sata) hard disks are in the same computer it would be the SCSI hard disk that will be numbered first in your BIOS. That should be fine for your setup, however this time your BIOS doesn't seem to have your sata drive as the first hard drive.

It looks like your 80.0 GB  IDE hard disk is empty, according to your fdisk output.
Your fdisk output shows your IDE hard disk as /dev/hdb too, I would have expected it to be /dev/hda normally. Maybe your CD drive or something is plugged in and jumpered as your primary master IDE drive, so your  BIOS is trying to boot that instead.  If that's right it would seem to explain a lot. 


Maybe you should go into your BIOS settings and check if your [hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority"). is right in there. You might need to change those settings there so your sata drive will be first. 
I realize your BIOS will probably be a lot different from mine, but that link should illustrate what I mean.
You already checked that your hard disk is in the boot sequence, but now we need to see if we can tell your computer which hard disk we're talking about.

Regards, Herman :D

---

### Post by Washington Irving on 2007-07-01
Ok cheers, I'll try that. I should probably mention that I have formatted the 80.0 GB drive to FAT32 and am using it as a backup for music and other files. I'm also trying to solve the problem of not being able to access the NTFS partition on the SATA drive simultaneosly to this boot problem. Hopefully I'll manage not to mess the whole thing up but I just thought I should explain my situation in case it has any bearing on this boot problem.

---

### Post by Washington Irving on 2007-07-02
I went into the BIOS and saw the hard disk drive order you mentioned, changed it to the other disk and that sorted it out. Thank you very much for your help.

---

