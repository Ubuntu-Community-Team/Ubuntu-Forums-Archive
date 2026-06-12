---
title: "Questions about dd command"
date: 2013-07-31
forum: General Help
---

### Post by rockymin on 2013-07-31
Hi,
  I'm looking to clone the hard drive of my Ubuntu server and was looking at the dd command.  I am planning to clone it to another hard drive attached via usb.
  I was wondering 2 things, first, can it be run while Linux is running or do you have to run it after booting to LiveCD?  Second, does the destination drive have to be partitioned beforehand or will dd create partitions as needed?
  The drive I am planning to clone has several partitions on it besides the primary Linux one.  I've used Ghost on Windows machines and it will create any needed partitions on an unallocated drive so I wondered if dd will do this as well.
  Also, if it can be run a running server, does it take up a lot of resources and slow the machine down?  Again, with Ghost, I have run it from Windows without booting to a Ghost CD and it doesn't slow anything down at all. So I was just wondering if dd was that way too.

Thanks.

---

### Post by sudodus on 2013-07-31
***dd*** is one alternative. ***Clonezilla*** another one. I use both of them. Clonezilla only copies the used part of each partition. I stopped using ***Ghost*** many years ago.

1. You should not run the system you are cloning. You should not even have any partition mounted on the drive you are cloning.

2. No, the destination need not be partitioned, when you clone the whole drive.

But the destination must be at least the same size (not smaller than the source).

You can make backups while a system is running, for example with ***rsync***, but some files that are actively used by the system will change during the process, so you do not get an exact cloned copy of the system at one particular state.

Many people back up their data and/or systems with rsync with or without a graphical user interface.

-o-

But for cloning, I suggest that you use dd or Clonezilla. dd is nick-named 'disk destroyer' because it does what you tell it to do without any questions. So if you tell it to overwrite your source ... so you must check and double-check, that you have the input device and the output device correctly defined. Use the following commands to help identifying the drives and partitions

```
 sudo fdisk -lu
```
```
 sudo parted -l
```
```
 sudo blkid
```
```
 df
```

You can run dd from a live system booted from an Ubuntu desktop install CD/DVD/USB drive.

Clonezilla has these checks built into the live system. You can download the iso file and make a boot CD or USB drive.

---

### Post by rockymin on 2013-07-31
Thanks for the reply, sudo.  I have already downloaded and created a clonezilla CD.  The server currently has a 500GB drive, the primary partition is 430GB and there's currently 100GB in use.  The destination is a 750GB drive.  

I wanted to be able to clone the drive while the server is running because there are websites and stuff running on the server that I didn't want to have down for a long time.  Approximately how long do you think a clonezilla would take to do the process?  

I'm still kinda new to Linux and I really don't understand why all these backup utilities need the server to be booted from a CD in order to be used.  I've been able to clone Windows machines while they are in use with no issues, why can't it be like that for Linux?

---

### Post by sudodus on 2013-07-31
You asked about cloning. So I answered about cloning.

But I also hinted, that backup with rsync  or other similar tools can be done while the computer is running. But you will not get a complete and perfect clone.

There may be advantages to use professional software. Are you sure that you get a perfect clone with the tool in Windows, when it is running? And you cannot switch off the computer. In that case I suggest that you continue using your tool in Windows for this task.

It is good to combine cloning and incremental backup:

1. A cloned disk or a disk with an image, from which you can restore a system that is exactly like the original one. This is done when booted from a live drive.

2. A frequent incremental backup system, for example copying all important directories every night. This is done as a cron job (started automatically at a certain time (typically 1 o'clock at night).

-o-

The time depends on the write speed and if you use compression of the cpu speed.

If you have an internal drive, or eSATA or USB 3 drive, you have rather high writing speed, but USB 2 is much slower, particularly when writing many small files. Depending on the circumstances the speed might be between 4 MB/s and 100 MB/s, so 100 GB would need between 1000 s (~ 17 minutes) and 25000s (~ 7 hours).

---

### Post by oldfred on 2013-07-31
Note that dd will copy the entire 500GB including all empty space, so it will be a lot slower. 

You also cannot mount both drives after copy as UUIDs and everything is identical, you have to go back and edit UUIDs, grub and some other settings to be able to mount old drive.

---

### Post by VMC on 2013-07-31
[Partclone]("http://partclone.org/") can do the job , which Clonezilla uses.

```
Example:
 === CLONE===
$ sudo su
# partclone.ext4 -c -s /dev/sdaX | gzip [or pigz] -c --fast>image.gz
=== RESTORE===
# zcat *image.gz*|partclone.ext4 -r -o /dev/sdaX
```

sudo apt-get install partclone

---

