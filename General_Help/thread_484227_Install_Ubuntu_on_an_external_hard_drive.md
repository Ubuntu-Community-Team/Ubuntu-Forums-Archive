---
title: "Install Ubuntu on an external hard drive"
date: 2007-06-25
forum: General Help
---

### Post by IJustConverted on 2007-06-25
I tried Ubuntu from a Live CD and I was really impressed. I really want to install it now and play with it and slowly convert to it. The problem is, I don't have too much empty space on my laptops hard drive. I have about 20GB of space left. I want to do one of two things:

1. Install Ubuntu on an external hard drive and have it run off of that. Has anyone done this and if you have, did you notice and noticeable performance bottlenecks due to the USB/Firewire interface?

2. I can also add a partition to my hard drive for all my personal data, install Ubuntu on the same hard drive, and have both Windows and Ubuntu share the same personal files off of the new partition. This way I can go back and forth between the two OS's very easily. Are there any issues with this?

I want to know what the experienced users here would recommend and if there are any problems I will run into. 

I need advice on one more thing and that is how much space to allocate for the swap, ext3 (I think that's what it was called) and whatever other partition I will need for Ubuntu. My system has 2GB of ram. I will do some development, office work, surfing, CAD design (if possible), DVD authoring (if possible), etc...

Any help would be appreciated and please offer your advice as soon as you can. I am very eager to install Ubuntu and start working with it.

Thanks in advance.

---

### Post by IJustConverted on 2007-06-25
Anyone?:?:

---

### Post by floke on 2007-06-25
Alrighty...

(1) Yes - and No
(2) Yes - as long as the document storage partition is FAT32 or NTFS - if its NTFS then you need the NFS-G3 thingy installed (its not called this but its something like it) to write to NTFS partition from Linux - its very easy to set up so no worries there.

I would go for around 10Gs for the root partition - this will also include a /home partition - but if you keep your key docs etc. on a separate partition then you can just use that too - actually you could just leave all your stuff in your NTFS partition and go over and use it from ubuntu whenever you needed to.

** EDIT - AutoCAD works fine through Wine as far as I could tell **

---

### Post by logos34 on 2007-06-25
> 1. Install Ubuntu on an external hard drive and have it run off of that. Has anyone done this and if you have, did you notice and noticeable performance bottlenecks due to the USB/Firewire interface?

You can search the forums--plenty of threads on it.  Works fine but is harder to configure.  I doubt you'll notice the speed diff in everyday use (I clocked my ide drive on a usb caddy at 34 MB/s vs. 54MB/s when connected internally, but I really don't notice it all that much.  Make SURE your lappy BIOS supports booting to USB device, otherwise forget it unless you want to use a floppy workaround.

I personally like the setup where you leave the internal drive untouched and install ubuntu to the external usb, making sure to put grub on the MBR of that drive.  To make sure grub goes there and not the mbr on the internal you can just open up the back of the lappy and unplug the power cord or data cable to the drive, then install ubuntu.  After install reconnect and set the bios to boot the usb drive first: if its connected/turned on, you go into grub, if not the bios skips the internal drive.  Just add fstab entries to ubuntu so windows paritions mount (or like the last poster said, get ntfs-3g) and away you go.

have fun!

---

### Post by floke on 2007-06-25
Or you could just use the alternative installer and type /dev/sdb or /dev/hdb - according to whatever it is - wehen prompted where to install grub.

---

### Post by logos34 on 2007-06-25
> **floke said:**
> Or you could just use the alternative installer and type /dev/sdb or /dev/hdb - according to whatever it is - wehen prompted where to install grub.

yeah, and it's probably best to use the alternate install cd because it will prompt you where to install grub--a lot clearer than the live cd (I think with feisty yu have to click at the bottom of the "ready to instlal screen' on 'advanced button which allows you to override the default location.  When you come to the grub part on the alternate cd you wnat to type '**(hd1)**' or '**/dev/sda**' (or sdb if you're internal is sata--even if it is IDE feisty may still see it as a 'scsi' drive).  (hd1) because grub start counting at 0, and its the second drive.

The only reason I sometimes recommend unplugging it is because it seems like no matter what you say regarding 
hd1 or sda etc, first time linux users invariably get confused at this point in the install process and grub ends up on the mbr of the lappy internal!

---

### Post by floke on 2007-06-25
Good point.
To see what ubuntu sees your external as, plug it in while running a live cd, open the terminal and type 'sudo fdisk -l' - this will give you a list of your partitions and mounted drives - the sdb or hdb at the end will be the external - Remember, when asked where to put grub do not put any numbers in - i,e, not sdb1 or sdb2 - just sdb (or hdb as the case may be).

Good luck.

---

### Post by IJustConverted on 2007-06-25
> **logos34 said:**
> I personally like the setup where you leave the internal drive untouched and install ubuntu to the external usb, making sure to put grub on the MBR of that drive.  To make sure grub goes there and not the mbr on the internal you can just open up the back of the lappy and unplug the power cord or data cable to the drive, then install ubuntu.  After install reconnect and set the bios to boot the usb drive first: if its connected/turned on, you go into grub, if not the bios skips the internal drive.  Just add fstab entries to ubuntu so windows paritions mount (or like the last poster said, get ntfs-3g) and away you go.

have fun!

First of all, thanks to everyone who posted a reply. I really like the idea above. How big of a thumb drive would be ideal for this type of a setup. And as far as sharing the data between XP and Ubuntu, is creating a separate partition the best way to go? And as far as the breakdown of the different paritions, what would be ideal?

Thanks again.

---

### Post by logos34 on 2007-06-25
> 1. Install Ubuntu on an external hard drive and have it run off of that...

> How big of a thumb drive would be ideal for this type of a setup

So which is it --  external usb HARD drive, or usb stick?

---

### Post by IJustConverted on 2007-06-25
> **logos34 said:**
> So which is it --  external usb HARD drive, or usb stick?

I originally meant an external HD, but after the suggestion was made, I would love to do it off of a USB stick if possible (more portable). The only thing I'm concerned about is the size of the USB drive and the partition sizes.

---

### Post by logos34 on 2007-06-25
You could do usb stick in persistent mode (search the forums for threads).  But, yes, the size is a problem.

As for hard drive, everybody has a diff opinion on partitioning but mine is to just leave the internal as is and get ntfs-3g driver to enable read + write access.  Works fine--disregard the scare stories.  But I would make a separate ext3 /home partition on the external in addition to / and /swap.  10gb for / is fine, 1gb for /swap, rest for /home.  Get fs-driver for windows to read + write to ext2/3 and you're set.

edit: the reason for separate /home is that all your personal docs, data and settings go there, and remain untouched the next time your do a fresh install of the latest Ubuntu release (which is better than a doing an upgrade).

And the one advanteage to unpluggin the internal drive before install is that you will be able to boot right into ubuntu afterwards without the hassle ofediting your grub config in menu.lst.  All you need to do is add windows to the mix.

---

### Post by IJustConverted on 2007-06-25
> **logos34 said:**
> All you need to do is add windows to the mix.
Is this difficult?

---

### Post by logos34 on 2007-06-25
> **IJustConverted said:**
> Is this difficult?

It's easy.  You just add a windows entry to the bottom of menu.lst and a line or two to fstab file (so that linux mounts winxp).  So when you boot up with the external usb attached you get the grub menu, where you can choose ubuntu or windows (avoids having to change the bios when you want to go to windows while the usb is attached).  And as already mentioned when it's not attached you just default to the internal hard drive.  

note: I just thought I'd add that if this is a bus-powered 2.5" external usb hard drive (vs. the 3.5" desktop version), there are some issues (with some at least) of failing to be recognized by the bios in time at boot if they're running on bus-power. No problem if connected by ac adaptor to outlet.  Don't know much about the details but i've read some posts about it.  Just thought I'd pass that along.

---

### Post by IJustConverted on 2007-06-25
> **logos34 said:**
> It's easy.  You just add a windows entry to the bottom of menu.lst and a line or two to fstab file (so that linux mounts winxp).  So when you boot up with the external usb attached you get the grub menu, where you can choose ubuntu or windows (avoids having to change the bios when you want to go to windows while the usb is attached).  And as already mentioned when it's not attached you just default to the internal hard drive.  

note: I just thought I'd add that if this is a bus-powered 2.5" external usb hard drive (vs. the 3.5" desktop version), there are some issues (with some at least) of failing to be recognized by the bios in time at boot if they're running on bus-power. No problem if connected by ac adaptor to outlet.  Don't know much about the details but i've read some posts about it.  Just thought I'd pass that along.

I appreciate the heads up. It is AC powered, but I think I'm going to take the USB route. I think I will get a 4GB memory stick? Will that be enough? How about a 2GB?

---

### Post by tepegoz on 2007-06-27
Hi,
I installed ubuntu to my laptop on the external harddrive.  I am using ubuntu on 4 different boxes as desktop and server also, and believe me, there is no speed difference between installing on the external or internal harddrives.  External harddrives are really fast, and usb connection is fast enough.

---

### Post by I.know.nothing on 2007-12-16
> **logos34 said:**
> It's easy.  You just add a windows entry to the bottom of menu.lst and a line or two to fstab file (so that linux mounts winxp).  So when you boot up with the external usb attached you get the grub menu, where you can choose ubuntu or windows (avoids having to change the bios when you want to go to windows while the usb is attached).  And as already mentioned when it's not attached you just default to the internal hard drive... 
.
Ok, but how do I do that , sory about my newbeeness

I have just bought a 320Gb USB HDD and have no idea about what partitions to make

Thanks for the help

---

