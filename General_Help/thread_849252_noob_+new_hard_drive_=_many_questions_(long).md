---
title: "noob +new hard drive = many questions (long)"
date: 2008-07-04
forum: General Help
---

### Post by cbwaters on 2008-07-04
Hello,
I did try to search for some of these answers but I'm really new at this and it's hard to understand a lot of the posts.

Backstory:
I came into possession of an older PC and decided to try to build an Linux server as a place to store and back-up files to.  I want to have it act just like the server drive I have at work.  You know, it's in "My computer" and I can use it just like any other drive but it's somewhere else in the building.

Downloaded and installed Xubuntu  but it was REALLY slow on my computer for some reason.  I had it working but it was just too slow.  I decided I ddn't really need all that graphical stuff and installed the latest Server Edition.

I have that working and can access it with Putty from my PC.  I couldn't figure out how to see the drive in the server from my PC.  The how-to I was using started out with two drives in the server.  One for the OS and one for file storage so I got a second drive for the server figuring I'd just follow the instructions.

New 120GB drive out of the box and installed.  I used Fdisk to partition as one big drive. Seemed ok.

The how-to specified a NTFS drive so I found and installed a package to use mkfs.ntfs.  It didn't want to make a file system with the whole disk but I, in my infinate wisdom, forced it.

Now I appear to have four partitions that have problems.  "Table entries are not in disk order." "partition does not end on cylinder boundary."  "File system unknown." etc.

 
The questions:
If I want to use the drive as file storage from  XP, do I need to use NTFS?

Do I have to have several partitions on a 120GB drive?  I really only want to see one drive.

How do start over?  I tried to re-partition using fdisk but it said the partitions are already used.

Is there an easier way to do all this?

Thanks,
Cory

---

### Post by justleen on 2008-07-04
> **cbwaters said:**
> Hello,
The questions:
If I want to use the drive as file storage from  XP, do I need to use NTFS?

Do I have to have several partitions on a 120GB drive?  I really only want to see one drive.

How do start over?  I tried to re-partition using fdisk but it said the partitions are already used.

Is there an easier way to do all this?

Thanks,
Cory

- no, you dont need ntfs, thats just easiest. fat32 is natively supprted by windows as well. XP can read ext2/3 too, but you need a driver for that

- you need just 1 parition, if you want to see 1 drive

- to start over, umount the drive, and run fdisk again (delete the old partition first)

- an easier way is cfdisk, of parted or gparted..

---

### Post by cbwaters on 2008-07-04
thanks,
cfdisk wouldn't start because of a bad primary partition.  
gparted won't start either.  says gtk warning **: can't open display.

I typed parted /dev/sdb (the drive) and it runs.  looks a little easier to use but I'm afraid to do anything because I can't see yet if it's actually working on the drive I'm trying to mess with.  I'd hate to re-install the OS (again).

When I do get this disk cleaned up, how do I set it up correctly?

---

### Post by cbwaters on 2008-07-04
I think I got it.  Figured out how to see which drive Parted was looking at.
Once I deleated the partition, I was still unsure about how to do what I wanted in Parted but cfdisk woudl start now and I think I got it to do what I wanted. fdisk now shows one partition of the right size and file type.

Now to get it working and see it in windows...
Thanks,
cory

---

### Post by justleen on 2008-07-04
rihgt, there you go!

---

### Post by cbwaters on 2008-07-04
well not so fast...
I can't seem to mount the disk.
the how-to [http://www.howtoforge.com/ubuntu-home-fileserver-p3]("http://www.howtoforge.com/ubuntu-home-fileserver-p3") works ok until I try the mount -a.  I get "ntfs signature missing" The device doesn't have a valid NTFS...

argggg

wife wondering if I'll ever get this done.

---

### Post by rraj.be on 2008-07-04
post the output of this

```
sudo fdisk -l
```

---

### Post by cbwaters on 2008-07-04
I left out the bit about the drive with the OS on because that's Linus FS and it actually works

disk /dev/sdb: 250.0 GB. 250059350016 bytes
255 heads, 63 sectors/tracks, 3041 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk indentifier 0x00000000

device boot      start      end      blocks      ID   system
/dev/sdb1          1      3401     244196001     7    htfs/ntfs

---

### Post by cbwaters on 2008-07-04
sigh... two hours of fighting this problem and I still can';t mount the NTFS drive...

---

### Post by pavel989 on 2008-07-04
> **cbwaters said:**
> sigh... two hours of fighting this problem and I still can';t mount the NTFS drive...

im not too sure, but i think theres a package or lib u need to install. for one thing, id bet its the restricted package, if not, just go into synaptic and check out what comes up for ntfs (i think its like apt-get search ntfs)

im sort of trying to do the same, but I'm considering just ftp or sftp'ing to it. not sure yet, since im mostly using my second box as a proxy/webserver. i wanna know how this turns out.

---

### Post by cariboo on 2008-07-04
What error are you getting when you try to mount your ntfs partiton?

When posting results use code blocks as the make things easier to read. The code block icon is the # symbol.

Jim

---

### Post by cbwaters on 2008-07-04
> **cariboo907 said:**
> What error are you getting when you try to mount your ntfs partiton?

When posting results use code blocks as the make things easier to read. The code block icon is the # symbol.

Jim

If I type: mount -t ntfs /dev/sdb1 /media/store
I get:
"NTFS signature is missing
Failed to mount '/dev/sdb1': invalid argument
The divice 'dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?"

I'm really not sure what you mean by code blocks.  I'm retyping all the text myself so the format might get jumbled.

---

### Post by cbwaters on 2008-07-04
I guess what I need to know first is:  

When you're trying to install a brand new drive as a single storage place for Windows files, can you simply use cfdisk to create a single primary maximized NTFS partition?

Is there some other step I'm missing?  Something else I need to do before I can mount this disk?

  I have tried mkfs.ntfs but that's what screwed-up my partition table before.  Of course, I might not have been doing it right...

Thanks,
Cory

---

### Post by cbwaters on 2008-07-05
Tried mkfs.ntfs again overnight (it takes hours) and it works now. 
i think the problem the first time was that I ran mkfs on the whole drive "/dev/sdb" instead of the patition "/dev/sdb1".

So, I can now mount my new drive.

Cory

---

### Post by SeanONe on 2008-07-28
> **cbwaters said:**
> the problem the first time was that I ran mkfs on the whole drive "/dev/sdb" instead of the partition "/dev/sdb1".


Does everyone have to go through this painful process, can't someone please make the damn program warn us.

---

### Post by ingeva on 2008-07-28
> **SeanONe said:**
> Does everyone have to go through this painful process, can't someone please make the damn program warn us.

First of all, why on earth would someone use an NTFS system on a Linux machine? :)

There's a program called gparted that makes partitioning of hard disks very easy.
If it's not loaded (was not in my standard setup) it's easily installed with the Synaptic Package Manager (under the System menu).

To mount the disk use the mount command. Help is available.

To access files from a Windows machine, set up the SMB (Samba) filesystem and you'll be able to read (and write, if you define permissions for it). There's a separate setup for SAMBA of course, but there are good directions so it shouldn't be hard.

---

