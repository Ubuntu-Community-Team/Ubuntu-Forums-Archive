---
title: "Unable to boot, all files lost?"
date: 2015-02-08
forum: General Help
---

### Post by jonno-o on 2015-02-08
Hi there!

I came home and tried to turn my computer on but got the message no bootable device and was unable to boot into my ubuntu 14.04. I dual boot with windows 7 but cannot access that either, just a black screen with the error message. 

Usually what happens is a purple screen where there are a few options including ubuntu 14.04 and windows 7 and i choose one and it boots. 

I have since then made sure my bios settings are fast boot: off and the eufi settings are set to both eufi and the other one (sorry forget the name!) but all variations in my bios settings make no difference. Sometimes it shows my SDD in the boot options (i think thats my hardrive?) but sometimes not.. I took that back off my laptop and unplugged the harddrive then put it back in but no difference..

I've created a bootable usb stick and i now use my computer on a "try it now" live session.

I ran boot repair, the first time it said successful but then went to an empty screen with a loading wheel that then went on forever till my power cut out. (my laptops battery is dead, needs to stay plugged in).  The pastebin given to me for this 'successful' boot repair was [http://paste.ubuntu.com/9690854/](http://paste.ubuntu.com/9690854/)

When i turned the computer back on there had been no change, still black screen. i tried again and this time it said 'backup your files' and gave me a pastebin which said 'no partitions'

I've left it a few weeks and i just tried again with the boot repair and the pastebin also says 'no partitions': [http://paste.ubuntu.com/10133958/](http://paste.ubuntu.com/10133958/)

Does this mean all my files have been lost? on both windows and ubuntu? I dont mind about getting the two operating systems back, or the files I had on windows 7, I just really want to get back the files I had on the Ubuntu OS, it had all my photos and work and secure documents, some of which were encfs files i opened with cryptkeeper.

Is there any way of getting them back? massive disaster if I can't!

I'm on a samsung series 5 ultra laptop

Many thanks for any help you can give me!!!!

-Jonathan

---

### Post by Bashing-om on 2015-02-08
jonno-o; Hi ! Welcome to the forum;

A quick peek to get an idea if your files can be gotten easily:
boot the liveUSB to terminal, post back - Between Code Tags, please - the outouts of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
If 'fdisk' screams and hollers about this as a 'GPT' disk and can not read it, install gdisk:
```

sudo apt-get install gdisk
sudo gdisk -l /dev/sda
##additional disks ?##
sudo gdisk -l /dev/sdb

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

once we are assured we can retrieve the data, we look about trying to resolve the booting issue.

[INDENT][INDENT][INDENT]it's buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jonno-o on 2015-02-09
Hi Bashing-om,

thanks so much for your reply. The results of those terminal commands are:

ubuntu@ubuntu:~$ sudo fdisk -lu

```

Disk /dev/sdb: 8462 MB, 8462008320 bytes
255 heads, 63 sectors/track, 1028 cylinders, total 16527360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01b3cc25

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    16527359     8263648+  83  Linux
ubuntu@ubuntu:~$ 

```

and 

ubuntu@ubuntu:~$ sudo parted -l


```

Error: /dev/sda: unrecognised disk label                                  

Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 8462MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8462MB  8462MB  primary  ntfs         boot

```



I think i've got that right.. thanks for your help!

-Jonathan

---

### Post by Bashing-om on 2015-02-09
jonno-o; Yuk .

There is nothing good I can say about this. If 'fdisk' and 'parted' can not see that hard drive, you do have a serious problem.
EDIT: Does bios - in the set-up utility see the hard drive ?
Open up that box and check cables, for bad connections.
Nothing amiss then ->
Next is to see if a recovery tool, testdisk, can see that hard drive. But do not hold your breath.
From your liveUSB:
In Software Sources, enable the universe repository, and
```

sudo apt-get install testdisk

```
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) <- written in a user-friendly way and introduces you to testdisk in a gentle way:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

I can not see any luck, but maybe
[INDENT][INDENT]let's see what testdisk sees
[/INDENT][/INDENT]

---

### Post by jonno-o on 2015-03-18
hey Bashing-om, im still using this computer in liveusb mode and have found some time to try and get back my files! i am using testdisk and it was able to see I had two partitions one which i knew to be my windows dual boot and one i knew to be my ubuntu partition. I then pressed 'write' in order to "write partition structure to disk" thinking i was almost home and dry but it came up with the error: 'write error' and no more info.. any thoughts? sorry i know this is a long time ago for you now.. is it hopeful that it at least acknowledges the partitions are there?

---

### Post by Bashing-om on 2015-03-18
jonno-o; Sorry;

I do not have the experience with testdisk to advise.

Perhaps others will respond.

[INDENT][INDENT]no-it all, not
[/INDENT][/INDENT]

---

### Post by pmi2 on 2015-03-18
I think you need to know what kind of disk drive you have, first.  TestDisk will tell on like the first or second screen what it found, and it better be what you have in the machine, or don't run it.

Was TestDisk run with sudo?  If not, certain things (like writing to it) may not work.  

Before you get to that point though, writing anything, I think there is an option to list the files found, and save them (?)  Did you try that?

Not being able to write anything to a disk does not mean you can't recover files from it.

In general, if you got as far as you say in the post above, you should be able to recover files from the disk (but maybe not a bootable OS though).  DiskTest may recover files, but I am not sure it knows everything to recover a bootable system, given grub2, Windows, dual boot, etc.

You may not save a bootable partition, or even the disk.  If it has a bunch of bad sectors, or a faulty cache, your data may be recoverable, but the disk may still be toast.  

For example, in the past I "fixed" a drive temporarily by disabling the write cache, and every other option I could find in drive settings (in Ubuntu that would be accessible from "Disks"), and the drive was basically crippled for everything exept reading files, but we did get all the data off this way.

Also, if you can sometimes see your hard drive, but no always, your failure can be heat related, in which case, let the PC sit and cool off, and then boot and run TestDisk.

---

