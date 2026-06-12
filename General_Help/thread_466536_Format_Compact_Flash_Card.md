---
title: "Format Compact Flash Card"
date: 2007-06-06
forum: General Help
---

### Post by RelativelyQuantum on 2007-06-06
A quick question: how would I format a compact flash card using Gnome? Can I do this through Terminal, or is there a way to do it directly form the System menu?

---

### Post by arkham on 2007-06-07
First, you must make sure the card is not mounted - IIRC the defauls path for automounting is /mnt/media or similar - when the card is inserted you can run the mount command with no arguments to get a list of what is mounted and where.

Once that is taken care of you can use the mkfs command, probabaly the easiest one to remember is:

```
mkfs.vfat /dev/name
```

Where name is the device that corresponds to your flash drive.  If you care about such things mkfs.vfat is really an alias to mkdosfs and the usage i exactly the same.  As someone that often formats various different filesystems, I find the mkfs.* names eaier to remember :)

Hope it helps.

Arkham

---

### Post by RelativelyQuantum on 2007-06-07
Thanks alot! This is exactly what I needed. Looks like it'll get off the ground after all. :)

---

### Post by RelativelyQuantum on 2007-06-07
Now, the device's name contains spaces, and I get the following:
```

reece@Mycroft:~$ mkfs.vfat /dev/ATA SanDisk SDCFH-20
mkfs.vfat 2.11 (12 Mar 2005)
/dev/ATA: No such file or directory

```

Do I need to be root? Then I tried this:
```

reece@Mycroft:~$ mkfs.vfat /media/ATA SanDisk SDCFH-20
mkfs.vfat 2.11 (12 Mar 2005)
/dev/ATA: No such file or directory

```

and

```
reece@Mycroft:~$ mkfs.vfat /dev/ATASanDiskSDCFH-20
mkfs.vfat 2.11 (12 Mar 2005)
/dev/ATA: No such file or directory

```

Neither worked. Where do I go from here?

---

### Post by hillbilly on 2007-06-07
No when he said device name, he meant block device name. For e.g. /dev/sda1 or something like that. I'm not sure how you can identify what the device name for the compact flash card would be. I think using > sudo fdisk -l could help. Or wait for somebody else to guide you on this.

---

### Post by RelativelyQuantum on 2007-06-07
Thanks - I'll try that.

---

### Post by RelativelyQuantum on 2007-06-07
Escellent! 

```
/dev/sda. 
```

I appreciate the help.

---

### Post by RelativelyQuantum on 2007-06-07
```
reece@Mycroft:~$ mkfs.vfat /dev/sda
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: Will not try to make filesystem on full-disk device '/dev/sda' (use -I if wanted)

```
?

---

### Post by RelativelyQuantum on 2007-06-07
Wait - I believe that did it. I had missed the bit about the 'I' at the end of the command

---

### Post by borahshadow on 2007-06-07
I think you want to create a partition on the card and then make a file system on that 
try  mkfs.vfat /dev/sda1
ps I'm not an expert

---

### Post by mcduck on 2007-06-07
> **borahshadow said:**
> I think you want to create a partition on the card and then make a file system on that 
try  mkfs.vfat /dev/sda1
ps I'm not an expert

That's correct. You cannot format a disk, but you can format a partition. Most likely your card only has one partition, so it would be /dev/sda1.

You can also use fdisk to edit/format partitions. Just run 'sudo fdisk /dev/sda'. Or, if you feel better using a GUI tool, install GParted. (You may also want to turn off automounting of removable drives when working with this kind of things. The option is in System/Preferences/Removable Drives and Media)

---

### Post by RelativelyQuantum on 2007-06-07
Thanks for all the help!

I'm formatting this card is so that it can be used as a bootable device in a barebone machine. When I ran

```
mkfs.vfat /dev/sda
```

it seemed to have been formatted, so I'm not certain weather the entire disk was formatted or weather I still need to format specific partitions. What I do know for certain is that the machine I put it into treated it as a bootable drive, so whatever I did seems to suit my needs. :)

---

### Post by hillbilly on 2007-06-07
Its like this, /dev/sda is actually the name of the device, in this case the first device on the SCSI chain. So in a way you can say that /dev/sda is the port for the device. Now you cannot write onto a device without creating a filesystem on it (you can through low level read/write or something like that, but thats besides the point). 
So before you can enable a device to store data, it must have a filesystem as it is the filesystem that stores data. And to create a filesystem, you need to setup a partition. you can either create a big partition which encompasses all the memory of the device or you can create multimple partitions spreading the memory around. When you create a partition you append a number to the deive name. So in this case it would be sda1. 
So what you have to do now is setup partition /dev/sda1 as a vfat filesystem.

> sudo mkfs.vfat /dev/sda1 is what you want.

Edit: I have no idea about the mkfs.vfat command though. I just took it from the above post

---

### Post by RelativelyQuantum on 2007-06-09
I have to say, thanks for all the help. I've been able to format the card with one large partition in the vfat format, which makes all the rest I was trying to do possible :D

---

