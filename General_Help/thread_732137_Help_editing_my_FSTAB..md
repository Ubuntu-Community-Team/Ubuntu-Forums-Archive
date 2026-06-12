---
title: "Help editing my FSTAB."
date: 2008-03-22
forum: General Help
---

### Post by robfindlay on 2008-03-22
I'm not a total newbie but my FSTAB skills are rusty.

I Installed a new HDD and i've had to manually mount it by going under "my computer" right clicking the "disk" and mounting. 

Lately It's been losing read and write permissions.

And i get an odd error message when I try to unmount it. SOOOOO I reckon I should be in my FSTAB as it is used all the time. 

Here is a copy of my current FSTAB: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a8624a32-ae23-463c-964c-670fe892724c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=601b62b5-784d-4397-a66b-7390e9810425 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


Can't for the life of me remember which disk the 2nd one is that I've been manually mounting so here's the relevant part of the /dev/ dir:

brw-rw----  1 root   disk      8,   0 2008-03-22 13:36 sda
brw-rw----  1 root   disk      8,   1 2008-03-22 13:37 sda1
brw-rw----  1 root   disk      8,   2 2008-03-22 13:36 sda2
brw-rw----  1 root   disk      8,   5 2008-03-22 13:36 sda5
brw-rw----  1 root   disk      8,  16 2008-03-22 13:36 sdb
brw-rw----  1 root   disk      8,  17 2008-03-22 13:36 sdb1

Any help most appreciated! 

-R

---

### Post by unutbu on 2008-03-22
Please post
```
blkid /dev/sdb1
```

---

### Post by robfindlay on 2008-03-22
> **unutbu said:**
> Please post
```
blkid /dev/sdb1
```

Code: 
/dev/sdb1: UUID="9a4f5042-6840-429e-b385-ce6ef5a3f374" SEC_TYPE="ext2" TYPE="ext3" 





-R

---

### Post by unutbu on 2008-03-22
The line you wish to add to /etc/fstab should look something like this:

```
UUID=9a4f5042-6840-429e-b385-ce6ef5a3f374 /media/disk ext3 defaults 0 2
```

change /media/disk to whatever mount point do like, just make sure the directory exists. 

Change 'ext3' to whatever filesystem exists on the /dev/sdb1 partition, of course. (Ah, I see it is ext3 from the blkid output.)

---

### Post by unutbu on 2008-03-22
You'll have to reboot before it will work because 

```
/dev/disk/by-uuid/
```

does not yet have a special file created for the second hd. The file is created at boot time.

---

### Post by robfindlay on 2008-03-22
Here is what I added: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a8624a32-ae23-463c-964c-670fe892724c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=601b62b5-784d-4397-a66b-7390e9810425 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/disk/ UUID=9a4f5042-6840-429e-b385-ce6ef5a3f374 /media/disk ext3 defaults 0 2


It still does not mount, i have to manually right click the disk under "my computer" then it mounts it as disk-1 

And oddly now I have e-drive dir, which is empty.

---

### Post by robfindlay on 2008-03-22
Here's a screenshot of the error message I am getting when trying to mount or in other cases unmount the image.

[IMG]http://img517.imageshack.us/img517/5994/desktop032208gs6.jpg[/IMG]

---

### Post by unutbu on 2008-03-22
```
/dev/disk/ UUID=9a4f5042-6840-429e-b385-ce6ef5a3f374 /media/disk ext3 defaults 0 2
```

should be

```
UUID=9a4f5042-6840-429e-b385-ce6ef5a3f374 /media/disk ext3 defaults 0 2
```

---

### Post by robfindlay on 2008-03-22
> **unutbu said:**
> ```
/dev/disk/ UUID=9a4f5042-6840-429e-b385-ce6ef5a3f374 /media/disk ext3 defaults 0 2
```

should be

```
UUID=9a4f5042-6840-429e-b385-ce6ef5a3f374 /media/disk ext3 defaults 0 2
```

That did it, THANKS ALL!!!

Slainte Mhath!!


-R

---

### Post by robfindlay on 2008-03-22
> **robfindlay said:**
> That did it, THANKS ALL!!!

Slainte Mhath!!


-R


I spoke to soon, all the files have a 0 byte count. and I cant read or write to the drive.


-R

---

### Post by robfindlay on 2008-03-22
Bump, major help needed.......!

---

### Post by robfindlay on 2008-03-22
Out put from my dmesg

dmesg | tail
[  592.436907] EXT3-fs: unable to read superblock
[  754.039579] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  754.039591] end_request: I/O error, dev sdb, sector 65
[  754.040319] EXT3-fs: unable to read superblock
[  846.711683] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  846.711695] end_request: I/O error, dev sdb, sector 65
[  846.712419] EXT3-fs: unable to read superblock
[  886.041819] sd 0:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  886.041831] end_request: I/O error, dev sdb, sector 65
[  886.042700] EXT3-fs: unable to read superblock

---

### Post by unutbu on 2008-03-23
Hm. That's a little troubling. 
Please post

```
sudo fdisk -l
```

(That's an 'el' not a 'one' at the end).

---

### Post by robfindlay on 2008-03-23
> **unutbu said:**
> Hm. That's a little troubling. 
Please post

```
sudo fdisk -l
```

(That's an 'el' not a 'one' at the end).

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

---

### Post by robfindlay on 2008-03-23
At present the "new" drivve wont mount through the gui and I forget the cmd line to mount it through the terminal.


-R

---

### Post by unutbu on 2008-03-23
```
mount /media/disk
sudo fdisk -l

```

---

### Post by robfindlay on 2008-03-23
what do you reckon the problem is?

---

### Post by unutbu on 2008-03-23
I'm sorry rob but I'm going to have to go now as it's quite late over here.
I'll try to pick up here tomorrow.

---

### Post by robfindlay on 2008-03-23
Now I get this: 

sudo mount /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by robfindlay on 2008-03-23
Anyone else?  I have some critical data I need to get off this disk...!

---

### Post by unutbu on 2008-03-23
I think from what output I see so far that the partition on the new hard drive is not an ext3 filesystem. I'm confused by that because it seemed that blkid said it was ext3. 

If you can mount the partition, my groggy brain is thinking right now that it might be best to backup any data you have there and then reformat...

---

### Post by dcstar on 2008-03-23
Install the **pysdm** package and use that to do **all** of the work.

I am constantly amazed as to why people stuff around with manually doing things when there are perfectly functional GUI tools available.

---

### Post by unutbu on 2008-03-23
Try removing the line in /etc/fstab, reboot, and they mount manually the way you've done before.

If that doesn't work, then I'm afraid I'm at a loss for ideas. Unless someone can step forward with a solution, I'm starting to suspect your hard drive is suffering some kind of hardware failure.

---

### Post by robfindlay on 2008-03-23
remind me which of these is the root or "main" hard drive? 

brw-rw---- 1 root disk 8, 0 2008-03-22 13:36 sda
brw-rw---- 1 root disk 8, 1 2008-03-22 13:37 sda1
brw-rw---- 1 root disk 8, 2 2008-03-22 13:36 sda2
brw-rw---- 1 root disk 8, 5 2008-03-22 13:36 sda5
brw-rw---- 1 root disk 8, 16 2008-03-22 13:36 sdb
brw-rw---- 1 root disk 8, 17 2008-03-22 13:36 sdb1

pysdm  only shows SDA  with SDA1 and SDA5

and SDB shows nothing under it and it's entirely grayed out.

---

### Post by robfindlay on 2008-03-23
Well, it's staying "alive" long enough to let me get my stuff onto a USB drive.

Thanks everyone.

---

### Post by unutbu on 2008-03-23
Rob, /dev/sda1 is your root partition. I'm glad to hear you've managed to backup your data. If pysdm works for you, then that's great. 

Here is why I prefer the command line interface (CLI) over GUIs:
1) I can fix some problems without needing X to be working.
2) I like to know what's under the hood. 
3) I prefer being able to read config files like /etc/fstab.
4) I can write scripts using CLI.
5) I can take notes on what commands I've used easier than I can describe "I clicked here, then I clicked there..."
6) Once you understand the CLI you don't need bloated GUI apps.
7) I type fast but click slow :)

---

### Post by robfindlay on 2008-03-23
> **unutbu said:**
> Rob, /dev/sda1 is your root partition. I'm glad to hear you've managed to backup your data. If pysdm works for you, then that's great. 

Here is why I prefer the command line interface (CLI) over GUIs:
1) I can fix some problems without needing X to be working.
2) I like to know what's under the hood. 
3) I prefer being able to read config files like /etc/fstab.
4) I can write scripts using CLI.
5) I can take notes on what commands I've used easier than I can describe "I clicked here, then I clicked there..."
6) Once you understand the CLI you don't need bloated GUI apps.
7) I type fast but click slow :)

Well I had to keep rebooting to get the partition to stay active on one reboot the system halted and said I had to run fsck manually which i did, it fixed a crap-load of stuff, after that reboot the partion has stayed active so......I dunno....we'll see.

For now anything critical is going onto CD/DVD or  the USB drive.

-R

---

### Post by robfindlay on 2008-03-23
I think the drive is hosed....I'm going to try and repartion it reformat it and see what happens.

OR I might just re-image the whole box as some  other things are acting wonky.

Are there GUI tools for repartitioning and reformating so I can do it from the desktop? 

-Rob

---

### Post by robfindlay on 2008-03-23
Bump! 

Help! 

TIA

-R

---

### Post by fsmithred on 2008-03-23
Uh, it's been awhile since I've done an ubuntu install, but I'm pretty sure that the live cd has a gui partitioner in the installer. You have to select Advanced or Expert Partitioner, or something like that. Even the non-gui partitioner is not bad - cfdisk, if you wanted to call it up from command line. It's all point and click with the keyboard.

---

