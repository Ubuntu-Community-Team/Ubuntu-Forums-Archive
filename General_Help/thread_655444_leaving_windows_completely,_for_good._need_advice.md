---
title: "leaving windows completely, for good. need advice"
date: 2008-01-01
forum: General Help
---

### Post by agent pink on 2008-01-01
yeah i'm about to wipe it out clean from my laptop but...

- i'm on dualboot with XP right now, residing on another partition.
so, how do i wipe it out? if i just format that partition what about grub?

- there's one piece of software that doesn't have linux version neither run on wine so i guess i have to go XP under ubuntu. I need that damn thing because that's where all my money come from.
now i really don't have any idea about this, should I go virtualbox? vwmare? qemu? i've read many, way too many, threads here and pages from google and i still don't get it :confused:

-bad english
any idea how to deal with this? hehe :D

oh btw, i don't want to wipe everything out and reinstall ubuntu. well it's the best thing solution i think, install ubuntu on a blank harddisk, but no!

thx, anything, help, ideas, advice are welcome :)

---

### Post by dlegend on 2008-01-01
> **agent pink said:**
> yeah i'm about to wipe it out clean from my laptop but...

- i'm on dualboot with XP right now, residing on another partition.
so, how do i wipe it out? if i just format that partition what about grub?

- there's one piece of software that doesn't have linux version neither run on wine so i guess i have to go XP under ubuntu. I need that damn thing because that's where all my money come from.
now i really don't have any idea about this, should I go virtualbox? vwmare? qemu? i've read many, way too many, threads here and pages from google and i still don't get it :confused:

-bad english
any idea how to deal with this? hehe :D

oh btw, i don't want to wipe everything out and reinstall ubuntu. well it's the best thing solution i think, install ubuntu on a blank harddisk, but no!

thx, anything, help, ideas, advice are welcome :)

Using GParted in Ubuntu should let you reformat the XP partition if you want to remove it completely. It should be fairly easy and you won't have any chance of losing your existing Ubuntu install. You will have to remove it from the GRUB menu.lst file though if you reformat the XP partition.

But you just mentioned that theres some software in Windows that doesn't run in Wine? What application would this be?

---

### Post by AndyCooll on 2008-01-01
> yeah i'm about to wipe it out clean from my laptop but...

- i'm on dualboot with XP right now, residing on another partition.
so, how do i wipe it out? if i just format that partition what about grub?
You can wipe the partition using GParted. You'll probably need to edit Grub. As for your MBR, it depends on which OS you installed first. 

> - there's one piece of software that doesn't have linux version neither run on wine so i guess i have to go XP under ubuntu. I need that damn thing because that's where all my money come from.
now i really don't have any idea about this, should I go virtualbox? vwmare? qemu? i've read many, way too many, threads here and pages from google and i still don't get it 
Which you use is entirely your choice and all will quite happily enable you to create and run a "virtual" XP environment. VirtualBox and VMware are probably easier to use, Qemu is open-source, and there is a version of VirtualBox that is open-source too (and is the one that I use). Indeed there is a version of VirtualBox in the repositories, so it would be easy to install and get up and running.

:cool:

---

### Post by agent pink on 2008-01-01
> **dlegend said:**
> Using GParted in Ubuntu should let you reformat the XP partition if you want to remove it completely. It should be fairly easy and you won't have any chance of losing your existing Ubuntu install. You will have to remove it from the GRUB menu.lst file though if you reformat the XP partition.
ok, i got the /boot/grub/menu.lst 
that one right?
> **dlegend said:**
> 
But you just mentioned that theres some software in Windows that doesn't run in Wine? What application would this be?
marketiva streamster, heard of it?
i already googling and googling even before i install ubuntu and no workaround for this but virtual machine. any idea how to run it on emulator?
> **AndyCooll said:**
> You can wipe the partition using GParted. You'll probably need to edit Grub. As for your MBR, it depends on which OS you installed first.
MBR? Master Boot Record? and? :confused:
it's XP first ofcourse, preinstalled. sorry but i'm a complete noob on this.
> **AndyCooll said:**
> 
Which you use is entirely your choice and all will quite happily enable you to create and run a "virtual" XP environment. VirtualBox and VMware are probably easier to use, Qemu is open-source, and there is a version of VirtualBox that is open-source too (and is the one that I use). Indeed there is a version of VirtualBox in the repositories, so it would be easy to install and get up and running.

:cool:
yeah i found virtualbox and qemu on synaptics but no vmware. virtualbox then? (waiting **dlegend** :D)

thx folks :)

---

### Post by MrFSL on 2008-01-01
+1 for vmware.
Download the package from the vmware server website.

---

### Post by dlegend on 2008-01-01
I haven't done anything VM-related as my laptop isn't powerful enough for it but I'd try out vmware as I have heard it is good. I'm not sure about the MBR.

Some googling I found this article: [http://flagrantdisregard.com/index.php/2007/11/28/removing-windows-from-a-dual-boot-system/](http://flagrantdisregard.com/index.php/2007/11/28/removing-windows-from-a-dual-boot-system/)

I have to go right now so hope everything works well, or when I come back I can try helping some more.

---

### Post by AndyCooll on 2008-01-01
Which did you install last? XP or Ubuntu? MBR=Master Boot Record.

:cool:

---

### Post by dlegend on 2008-01-01
> **AndyCooll said:**
> Which did you install last? XP or Ubuntu? MBR=Master Boot Record.

:cool:

He installed Ubuntu last...

[quote=agent pink]
MBR? Master Boot Record? and?
it's XP first ofcourse, preinstalled. sorry but i'm a complete noob on this.
[/quote]

---

### Post by Jerry N on 2008-01-01
> **agent pink said:**
>   - there's one piece of software that doesn't have linux version neither run on wine so i guess i have to go XP under ubuntu. 

Have you tried Crossover? It seems to run more Windows programs than Wine but it is not free (~$40).

Jerry

---

### Post by maestrobwh1 on 2008-01-01
STOP!:confused:

Make an image of your disk first before you do anything f you have any kind of external storage device large enough to hold a copy of your Ubuntu OS

A free, but not so user friendly (not hard to figure out either though), but very powerful cloning program:
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

Then proceed and know:

If you completely REMOVE the partition AND RESIZE UBUNTU IN TO THE EMPTY SPACE, grub won't know where to find its configuration files and YOU WON'T BE ABLE TO BOOT so...

The EASIEST option: Reformat the XP partition, shrink it to some very small size (smallest allowed and still keep it) and forget it exists, and "grow" the  ubuntu partition into the empty space - this is perhaps safest.  

Next option, that is safe but needs more knowledge: leave it as a larger partition, and use it for storage.  If you change the type, say from NTFS, to Fat32, or EXT3, Ubuntu won't be able to read/write to it until you fix its entry in /etc/fstab.  If it is already Fat32, then just keep it that. You could keep it at NTFS, as I write to my NTFS partitions all the time using ntfs-3g.  Totally safe.  NTFS is great, like EXT3, because it has no file size limit.

Advantages of keeping a partition there: Grub will still be able to find its boot files because they will be on the same partition number.  Also, fstab will can still let ubuntu know where the swap partition is (if ubuntu installed itself on a logical partition, this won't probably change change).  If your ubuntu's root is on hda5 and the swap is on hda6, and XP is on hda1, then ubuntu is on a logical partition and this might not be an issue no matter what you do.

How to do this the best way: Using a  gparted live cd (you can't use gparted in Ubuntu to grow the partition it is on because a mounted partition is locked, but at any rate even if you could, I find it safer to work with every disk/partition unmounted):
[http://gparted-livecd.tuxfamily.org/index.php]("http://gparted-livecd.tuxfamily.org/index.php")
It loads a desktop with a partitioner, all graphical and nice.  Boot from it and resize as you want.

Or if you really want to remove the partition: It can be done, but you need some grub bootloader knowledge/instructions and know you may need to edit fstab to get ubuntu to recognize the swap partition.  Know that if you DELETE the partition completely, you probably won't be able to boot unless you know how to do these extra things.  I see this removing the entire partition as completely unnecessary because of your noob status and there seems to be no advantage I can think of.  And you seem to be needing more of a step by step process of what to do and expect.

---

### Post by g2g591 on 2008-01-01
if you didn't know, you CAN NOT install virtual windows from any recovery cds you recieved with your computer . If you want to install windows virtually, you must pickup a FULL (not upgrade, like those in Walmart or target) copy of windows running >$150 .

**Marketivia or the Wine appdb doesn't say it doesn't work on wine, just _TRY IT_, it might work, perhaps not perfectly, but it should work at least some.**

The good news is that Marketivia says in their FAQ that they have a version that will work under wine perfectly in development.

---

### Post by mdpalow on 2008-01-01
I think I might have missed something in this thread, but I'll respond anyway real quick.

VMware is really nice for that one special program you need that won't run in Linux. I've had it installed for some time and use it with no problems if/when I need to use a Windows program.

[Here's a good link for VMware.]("http://ubuntuforums.org/showthread.php?t=183209")

Good luck...

---

### Post by Jerry N on 2008-01-01
> **g2g591 said:**
> If you want to install windows virtually, you must pickup a FULL (not upgrade, like those in Walmart or target) copy of windows running >$150 

I haven't tried it with a virtual package but you can do a normal install of Windows XP from an upgrade disk **_IF_** you possess a legitimate Windows 98 disk.  You do not have to install Windows 98 but you will need insert the Win 98 disk when the XP install says it can't find a Windows program to upgrade.

Jerry

---

### Post by seachnasaigh on 2008-01-02
I understand leaving Windows, philosophically-speaking; however, I'm not 100% sure I understand your initial post completely.

As heretical a suggetion as it might seem, I'd urge you to consider leaving your Windows partition alone and just moving on, mentally. Boot into XP when you need your Marketivia application and let it go at that. Do you so badly need the disk space that XP is taking? How about creating a nice little storage space in there formatted in vfat or ext3 by using Ubuntu to resize that partition and create another? Or perhaps get yourself a nice little USB thumb-drive (4 GB models are pretty cheap!)

You've already indicated that XP came pre-installed with your computer; another poster has indicated (correctly) that recovery CD's won't typically install to a vmware partition (although yes, there is a workaround for this using an upgrade CD but it's not precisely free or easy or perfect). 

Were it me, I think I'd try VMWare on your current install before doing anything drastic with your XP partition, to see how/if it works for you ... particularly if your cash cow is tethered to your Windows installation.

Good luck and cheers!

---

### Post by agent pink on 2008-01-02
holly freyja!!! :shock:
slow down ppl, wait for me... lol
first, let me digest all that infos :D

thx everyone :)

---

