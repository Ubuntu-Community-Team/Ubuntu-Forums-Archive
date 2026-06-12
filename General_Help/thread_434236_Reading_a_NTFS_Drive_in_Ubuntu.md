---
title: "Reading a NTFS Drive in Ubuntu???"
date: 2007-05-05
forum: General Help
---

### Post by DisappearingBoy12@hotmail on 2007-05-05
Hi everyone! I made a covertion from Ubuntu back to Windows 8 months ago and now remember why I left in the first place. I wanna go back but I have about 50 Gigs of stuff on my windows drive that i wanna put on the Linux one without the use of DVDs if posible. Any suggestions on how I can do this?

---

### Post by jfinkels on 2007-05-05
> **DisappearingBoy12@hotmail said:**
> Hi everyone! I made a covertion from Ubuntu back to Windows 8 months ago and now remember why I left in the first place. I wanna go back but I have about 50 Gigs of stuff on my windows drive that i wanna put on the Linux one without the use of DVDs if posible. Any suggestions on how I can do this?

Mount the partition, then copy whatever you want to copy over :D

You might need the NTFS-3G driver if it is an NTFS formatted partition.

---

### Post by DisappearingBoy12@hotmail on 2007-05-05
Ok... first where do I get the drivers that I need... then how do I mount the drive? Thanks!

---

### Post by julian67 on 2007-05-05
```
sudo apt-get install ntfs-config
```

Agree to the dependencies offered and install. Then run NTFS Configuration Tool (it will be in the regular main menu under System) and check the box to enable write support for your drive. Done :) 

You might need to reboot.

---

### Post by jfinkels on 2007-05-05
To mount a partition, first you need to know its physical location, then you need to make yourself a mount point.

To find out where that partition is, type this:
```
sudo fdisk -l
```
And you will see a list of devices and partitions. For example, mine looks like this.
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11784    94654948+  83  Linux
/dev/sda2           11785       12161     3028252+   5  Extended
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris

```
Hard disks are named /dev/sda, /dev/sdb, /dev/sdc etc. if you are in Feisty (in Edgy, it may be /dev/hda, etc.).

Different partitions on each disk are numbered 1, 2, 3 etc. So the first partition on the first disk will be /dev/sda1, as you can see on my listing above. You're going to have to determine where yours is, or post the output of "sudo fdisk -l" and we can help you if you can't figure it out on your own.

Second, make a mountpoint (just a fancy name for a directory).
```

sudo mkdir /mnt/myotherpartition

```
You can name it whatever you want.

Then mount your partition at your mountpoint.
```

sudo mount /dev/sdX# /mnt/myotherpartition

```

I don't know if you have to specify some extra options with mount because of the ntfs-3g drivers (like some goofy type specification), but you can try that first and see if it works.

Now you should be able to read and write files from that partition. They are in /mnt/myotherpartition

---

### Post by waggygee on 2007-05-06
> **julian67 said:**
> ```
sudo apt-get install ntfs-config
```

Agree to the dependencies offered and install. Then run NTFS Configuration Tool (it will be in the regular main menu under System) and check the box to enable write support for your drive. Done :) 

You might need to reboot.

:~$ sudo apt-get install ntfs-config
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-config

Thats what I get when I enter the first command instructed

---

### Post by julian67 on 2007-05-06
> **waggygee said:**
> :~$ sudo apt-get install ntfs-config
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-config

Thats what I get when I enter the first command instructed

It's in the universe repository, probably you have not enabled universe. Enable it and reload the repos and it will install. 

I'm assuming you're using Feisty.  I don't know if it is in the repos for Edgy, Dapper, Breezy etc.

---

