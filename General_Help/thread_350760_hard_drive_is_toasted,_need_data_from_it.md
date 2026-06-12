---
title: "hard drive is toasted, need data from it"
date: 2007-02-01
forum: General Help
---

### Post by rajan on 2007-02-01
Hi, I have been trying to recover the data from my HD for a few days now. the problem started when i tried to update from breezy to dapper and something made the xserver crash. i couldn't get it started up (the error it said was something was wrong with the keyboard, but i don't really believe that because i could use the keyboard before) and now i can't even see the data with the live cd, knoppix, or trinity rescue utility. the drive says it has mounted because when i type "sudo mount /dev/hda5 /mnt" it tells me that either hda5 is already mounted or /mnt is busy. also, i have tried to use gparted and when i select hda, it says that it's unable to detect the filesystem because: the filesystem is damaged, the filesystem is unknown to libparted, or there is no filesystem. since i'm using linux and i did actually have a filesystem, it must be that the filesystem is damaged. 

How can i fix the filesystem? how would it have been damaged? the only thing I did was to go a bit into the reinstallation process with my breezy badger CD, but i didn't tell it to change the HD in any way. 

I really would like these files back and i don't have the 300 bucks that it would cost to have someone professionally do it. thanks a lot for any help i get.


rajan

---

### Post by Bigbluecat on 2007-02-02
It's not clear what the real problem here is. It sounds like you can partially boot Ubunutu but it fails part way.

I don't think we have really diagnosed this problem yet. There are a couple of things we can try.

First - can you run a live CD and in a terminal type:
```
sudo fdisk -l
```

This will let us see what your disk and partition structure looks like. Post the output and tell us if anything looks wrong.

A corrupted partition table could mess things up and what you thought was HDA5 is no longer HDA5.

So. To find out if it is a corrupted partition table you can use a utility called Testdisk. It is included on the GParted LiveCD:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

[http://mirror.href.com/thestarman/testdisk.html](http://mirror.href.com/thestarman/testdisk.html)
[http://www.pcstats.com/articleview.cfm?articleid=1139&page=8](http://www.pcstats.com/articleview.cfm?articleid=1139&page=8)

The third link above although for windows looks to be a useful step by step guide. 

Diagnosing disk problems from a live CD is quite useful as the drive iteself is not mounted.

I use this method to successfully reconstruct a windows drive after a bad crash that corrupted the partition table. Needless to say after that windows would not boot but Testdisk saved me.

A word of warning. Anyhting like this runs the risk of losing data (if it is not lost already). If you can back up first. I had all my windows drive backed up on an external drive so was not too worried.

Hope this helps and let's see if we can find a way through for you.

---

### Post by rajan on 2007-02-03
output from sudo fdisk -l

```

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/hda: 40.0 GB, 40020664320 bytes 
255 heads, 63 sectors/track, 4865 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes

 Device Boot Start End Blocks Id System 
/dev/hda1 * 1 31 248976 83 Linux 
/dev/hda2 32 4865 38829105 5 Extended 
/dev/hda5 32 4865 38829073+ 8e Linux LVM 
ubuntu@ubuntu:~$

```
and......
output from dmesg | tail

```

[17180173.444000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0. 
[17180173.444000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode 
[17180173.444000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode 
[17180173.732000] [drm] Setting GART location based on new memory map 
[17180173.732000] [drm] Loading R300 Microcode 
[17180173.732000] [drm] writeback test succeeded in 1 usecs 
[17180613.564000] SQUASHFS error: Can't find a SQUASHFS superblock on hda2 
[17180690.836000] attempt to access beyond end of device 
[17180690.836000] hda2: rw=0, want=4, limit=2 
[17180690.836000] EXT3-fs: unable to read superblock

```

just got a new HD so i'm going to be installing that while i try to recover the data off my old HD. still open to hints/hunches or anything. thanks again.

---

### Post by r4ik on 2007-02-03
Have a look at Mondo.

Mondo is reliable. It backs up your Debian GNU/Linux server or workstation to
tape, CD-R, CD-RW, NFS or hard disk partition. In the event of catastrophic
data loss, you will be able to restore all of your data [or as much as you
want], from bare metal if necessary. Mondo is in use by numerous blue-chip
enterprises and large organizations, dozens of smaller companies, and tens of
thousands of users.

Mondo is comprehensive. Mondo supports LVM, RAID, ext2, ext3, JFS, XFS,
ReiserFS, VFAT, and can support additional file systems easily. It supports
adjustments in disk geometry, including migration from non-RAID to RAID. Mondo
runs on all major Linux distributions and is getting better all the time. You
may even use it to backup non-Linux partitions, such as NTFS.

Perhaps it is what you want.
It can be found in Synaptic.

Good luck !

---

### Post by Bigbluecat on 2007-02-03
The output from DMESG seems to indicate a problem on /dev/hda2. You may be able to fix this with testdisk. It is probably worth running the analyse function in testdisk to see what it says about your drive anyway.

---

### Post by rajan on 2007-02-03
ok i'm running 6.06 right now on a new HD and i will be adding the old HD as a slave soon. i'll be giving your suggestions a shot as soon as i can find a power cable to hook into the slave drive (i only have 1 power cable for the two of them for some reason). thanks for the help.

raj

---

### Post by rajan on 2007-03-17
back at it... so if anyone is paying attention to this thread anymore, i have a few updates. i am still trying to get the hard drive mounted but without luck. i now have my hard drive in the slave position (although i think it's still switched to "master" on the actual drive), and it still doesn't boot. this hasn't helped me get data out of the old HD, but it has allowed me to use my computer with dapper (which, by the way, kick a**). testdisk did not fix the problem, but i had a few problems with it so it could be my fault.

my fdisk -l is:

```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14405   115708131   83  Linux
/dev/hda2           14406       14593     1510110    5  Extended
/dev/hda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32        4865    38829105    5  Extended
/dev/hdb5              32        4865    38829073+  8e  Linux LVM

Disk /dev/sda: 257 MB, 257474560 bytes
65 heads, 32 sectors/track, 241 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         242      251423+   4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(241, 49, 31)

```

and my dmesg | tail is
```

[17179611.612000] NET: Registered protocol family 31
[17179611.612000] Bluetooth: HCI device and connection manager initialized
[17179611.612000] Bluetooth: HCI socket layer initialized
[17179611.632000] Bluetooth: L2CAP ver 2.8
[17179611.632000] Bluetooth: L2CAP socket layer initialized
[17179611.700000] Bluetooth: RFCOMM socket layer initialized
[17179611.700000] Bluetooth: RFCOMM TTY layer initialized
[17179611.700000] Bluetooth: RFCOMM ver 1.7
[17179620.672000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17185436.236000] cdrom: open failed.

```

the "FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!" part kinda disturbs me because one of the problems that i saw while researching my problem was that "Keyboard" was not the same as "keyboard." the problem comes when some of the startup files are looking for "keyboard" and only finding "Keyboard." I'm not sure if this could be the problem, but i did notice something about a "keyboard and mouse not found" error. 

TIA

---

### Post by Bigbluecat on 2007-03-18
Rajan,

Took my eye of of this for a while.

We could try to manually boot the kernel. It's not that hard but I have no idea if it will do any good. May throw up some alternate error messages.

You will need SuperGrubDisk:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

And Herman's guide on using the grub command line interface:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I take it that you can't just mount the drive and copy the data over.

---

### Post by rajan on 2007-03-18
Great to hear from you again, BigBlue! I looked over the guides and everything for super grub disk and I have everything ready to go now and I'm about to reboot with the SGD CD. 

You're right, I can't mount the other HD at all. This is strange because I should really be able to mount it, even if I couldn't display any of the data on it:

```
rajan@paravati:~$ mount /dev/hdb
mount: can't find /dev/hdb in /etc/fstab or /etc/mtab

```

and:

```
rajan@paravati:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
rajan@paravati:~$

```

---

### Post by gray-squirrel on 2007-03-18
You may need to add mount points to [FONT="Courier New"]/etc/fstab[/FONT].  Try adding something like ```
/dev/hdb1       /media/hdb1               ext3    defaults,errors=remount-ro 0       1
```

I'm not familiar at all with LVM, so I don't know how to add that in. . . although if you have an older copy of [FONT="Courier New"]fstab[/FONT] (from before the new hard disk addition) you can cut and paste the line which has the mount point for [FONT="Courier New"]/dev/hda5[/FONT] into your current [FONT="Courier New"]fstab[/FONT] and change it to read [FONT="Courier New"]/dev/hdb5[/FONT].  Those changes should get your ext3 and LVM partitions from your old hard disk mounted.

Once you make the changes, type [FONT="Courier New"]sudo mount -a[/FONT] in a terminal.  That way you can see if the partitions mount without having to reboot.

---

### Post by rajan on 2007-03-18
BigBlue, I tried the super grub disk and it told me a lot of things that I had hoped weren't the case. I tried to boot the MBR first and it spit this out:

```
root (hd0,0)
filesystem is ext2fs, partition type 0x83
kernel /vmzlinuz-2.6.12-10-686 root=/dev/mapper/ubuntu-root ro quiet splash
error 15: file not found
press any key to continue...
```

then i tried to boot partitions and it gave me an error 13: invalid or unsupported executable format, but that also happened when i tried to boot the HD that's actually working, so i'm not sure if that's really an error. 

the real piece of bad news was that when i went to boot directly, it searched for a few files, including a .lst file and a few others. it only found the files that were on the working HD so i only had those to choose from and i could only boot the working HD. 

Gray-squirrel,
 I added the line that you suggested to my fstab file and it seems to be doing something. I just can't figure out how to access the files inside the hdb now. here's what i did so far:
```
rajan@paravati:~$ sudo mkdir /media/hdb1
rajan@paravati:~$ sudo mount -a
rajan@paravati:~$ ls /media/hdb1
abi-2.6.12-10-386     grub                      System.map-2.6.12-10-386
abi-2.6.12-10-686     initrd.img-2.6.12-10-386  System.map-2.6.12-10-686
abi-2.6.12-9-386      initrd.img-2.6.12-10-686  System.map-2.6.12-9-386
config-2.6.12-10-386  initrd.img-2.6.12-9-386   vmlinuz-2.6.12-10-386
config-2.6.12-10-686  lost+found                vmlinuz-2.6.12-10-686
config-2.6.12-9-386   memtest86+.bin            vmlinuz-2.6.12-9-386
rajan@paravati:~$

```

where hdb is the problematic hd and it's mounted in /media/hdb1 from the line
```
/dev/hdb1       /media/hdb1     ext3    defaults,errors=remount-ro 0       1
```
that i added to my fstab

Now i can't figure out where the important files are in the /media/hdb1 directory (contents displayed above). Thanks a lot for the help so far and looking forward to any more tips you have.

---

### Post by gray-squirrel on 2007-03-19
Did you also include the line for mounting [FONT="Courier New"]hdb5[/FONT] in [FONT="Courier New"]/etc/fstab[/FONT]?  It was the LVM partition you were talking about earlier.

---

### Post by rajan on 2007-03-19
No, I hadn't done that. Thanks. However, when I do put that code in, my fstab reads:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/hdb1     ext3    defaults,errors=remount-ro 0       1
/dev/hdb2       /media/hdb2     ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       /media/hdb5     ext3    defaults,errors=remount-ro 0       1

```

and when I type sudo mount -a I get:

```

rajan@paravati:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: /dev/hdb5 already mounted or /media/hdb5 busy

```

so that means bad things I guess. 

dmesg | less gives me (along with a lot of other things):
```

[17179618.028000] cdrom: hdc: mrw address space DMA selected
[17179618.856000] ISO 9660 Extensions: RRIP_1991A
[17179619.472000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180954.784000] kjournald starting.  Commit interval 5 seconds
[17180954.796000] EXT3 FS on hdb1, internal journal
[17180954.796000] EXT3-fs: mounted filesystem with ordered data mode.
[17180982.616000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17180982.616000] kjournald starting.  Commit interval 5 seconds
[17180982.616000] EXT3 FS on hdb1, internal journal
[17180982.616000] EXT3-fs: mounted filesystem with ordered data mode.
[17211158.580000] attempt to access beyond end of device
[17211158.580000] hdb2: rw=0, want=4, limit=2
[17211158.580000] EXT3-fs: unable to read superblock
[17211407.992000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17211407.992000] kjournald starting.  Commit interval 5 seconds
[17211407.992000] EXT3 FS on hdb1, internal journal
[17211407.992000] EXT3-fs: mounted filesystem with ordered data mode.
[17211408.000000] attempt to access beyond end of device
[17211408.000000] hdb2: rw=0, want=4, limit=2
[17211408.000000] EXT3-fs: unable to read superblock

```

Thanks again for the help. I'm willing to take any crazy chance right now with this HD as I've become comfortable with the idea that I'll never see the data on it again. I just would like to know what happened.

---

### Post by gray-squirrel on 2007-03-19
Perhaps it was due to it not being mounted correctly still.  I was going to suggest [[FONT="Courier New"]ddrescue[/FONT]]("http://www.gnu.org/software/ddrescue/ddrescue.html"), but I just want to make sure we try to mount this partition successfully.

I don't use LVM, so I know little about it.  However, I did find an [example]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch27_:_Expanding_Disk_Capacity#Update_The_.2Fetc.2Ffstab_File") of how they are mounted in /etc/fstab: ```
/dev/lvm-hde/lvm0   /home      ext3    defaults        1 2
```

Where it says [FONT="Courier New"]/dev/lvm-hde/lvm0[/FONT] you would replace that with the logical volume you used before the hard disk switch.

---

### Post by adrian15 on 2007-03-19
[QUOTE=rajan;2320314]
```

rajan@paravati:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: /dev/hdb5 already mounted or /media/hdb5 busy

```

so that means bad things I guess. 

dmesg | less gives me (along with a lot of other things):
```


I think you should try:

[code]
sudo mkdir /media/hdb5

```

before trying to mount it. If it fails then to mount you have a problem and you should use fsck carefully.


adrian15

---

### Post by Bigbluecat on 2007-03-19
Adrian15,

I don't think booting the MBR will work as you have moved the hard disk. So it is likely that grub and the menu.lst are poiting to incorrect HD and partitions.

Try manually booting the kernel. The instrucions are on Hermans page. It is not hard. You get to the grub command line from SuperGrubDisk.

These are the instructions on interrogating the system and booting. In your case you will have two linux systems. One on each disk. Don't worry if it looks complex. I did this a couple of times as a complete newbie. You learn a lot about boot systems and how grub works this way.


Unfortunately it won't let me paste the relevant solution here - too long.

Go to:

[http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)

And follow the instructions about using grub to interrogate the system and then directly boot the kernel. It's fun :O)

---

### Post by rajan on 2007-03-20
Adrian15, I can't mount any volume without creating a mountpoint first. So if the directory /media/hdb5 didn't exist, then an error message stating so would have come up. 

Gray-squirrel, I tried changing the lines in my fstab to reflect the lines from that example, but it still gave me the same error. I didn't, however, specify the volume where I want to be inside the LVM, so that is something that I should do. I can't do it though because I don't have the volume information from that HD (yet another thing I should have backed up). 

BigBlue, I'm getting at that manual boot right now. 

Thanks for the tips everyone... the only thing that made my full day of work on a M$ OS better was being reminded of my ubuntu baby at home.

---

### Post by FuZ3 on 2007-03-20
I can guarantee you that if

A. The hard drive is the problem

and

B. The drive is not physically damaged

then SpinRite can fix it.

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

It is a commercial product but it's only $80(as opposed to the $300 you said you weren't willing to pay) and its a good investment anyways.

Or go ahead and continue whatever you were doing.

---

### Post by rajan on 2007-03-20
well, that was much more than I bargained for... the directions are really clear and easy to follow and i finally have pinpointed a significant problem stopping me from booting normally. 

i went in using SGD's command line interface as described in Herman's site and the following happened:

geometry (hd1) <---- hd1 is the "bad" HD
produced the following: 
partition num 0, filesystem is ext2fs, partition type is 0x83
partition num 4, filesystem is unknown, partition type is 0x8e

then root (hd1,1) gave me: filesystem type unknown, partition type 0x5

root (hd1,4) gave me similar output

kernel /vmzlinuz *tab autocomplete* didn't work because grub was not able to mount the hd1. 

I think I have to reconstruct the file where it says the filesystem type, if that is possible. I have heard that there are ways to reconstruct filesystems and I might have to do that as well, if it's even possible. 

for now, a few hours of sleep... :)

---

### Post by Bigbluecat on 2007-03-20
Grubs CLI is very useful for boot diagnostics.
OK.

What was the result of find /boot/grub/stage1. This should return two locations - the working partition and the one on HD1. The output of this is used for root.

Also curious as to why you used root (hd1,1) and it was not root(hd1,0) for the first partition of hd1.

So there is certainly a problem with the hard drive. Without going back through the thread have we tried a simple fsck on the drive. I have not run fsck on an unmounted drive but I think there is a way to do it.

---

### Post by rajan on 2007-03-21
ok, the 
```
find /boot/grub/stage1
```
returned only a file on hd0

you're right, the hd1 partition should have been 0, not 1. when i reentered (hd1,0) instead of (hd1,1) i got some strange errors. they are displayed on the screenshot attached here. and when i say "screenshot," i really *mean* screenshot.

i'm going to read up on grub's stage1...

Here's something from an fsck that I applied to my unmounted volume. 
```
rajan@paravati:~$ sudo fsck /dev/hdb1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/boot: clean, 40/124496 files, 42732/248976 blocks

```

according to this:
[http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds2/fsck.htm#HDRA10192CC1](http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds2/fsck.htm#HDRA10192CC1)
you can run an fsck on an unmounted volume. i have heard [read] that there is possibly some problems running fsck on LVM, but its replacement, vgck, doesn't seem to do anything:

```

rajan@paravati:~$ sudo vgck /dev/hdb1
  Volume group "hdb1" not found
rajan@paravati:~$ sudo vgck /dev/hdb
  Volume group "hdb" not found

```

---

### Post by Bigbluecat on 2007-03-21
Sounds like the 1st partition is lost. My only suggestion to try to recover this is TestDisk but you already tried that.

You could look at the devices map. I think it is /boot/devices.map or it is in /boot/grub. Not at my linux just now so cannot check.

Still if it cannot find the kernel files there is not much the system can do - whether it is pointing to the right locations of not.

---

### Post by rajan on 2007-03-21
ok, thanks a lot for your help, BigBlue. I really don't care about my data anymore, I just wanted to learn more about my system, and you definitely helped me with that. There's a few more last-ditch efforts I'm going to try, but it seems that I will have another 40 GB of empty space soon. 

thanks again for everything, everyone.

---

### Post by Bigbluecat on 2007-03-21
Just noticed on the screenshot with errors on it there is a kernel panic.  That suggests that it found a kernel to try an boot.

Doesn't help us much though. I'm at a loss as to what to suggest next. Sorry we couldn't recover it.

Good luck.

---

### Post by adrian15 on 2007-03-22
> **rajan said:**
> 
geometry (hd1) <---- hd1 is the "bad" HD
produced the following: 
partition num 0, filesystem is ext2fs, partition type is 0x83
partition num 4, filesystem is unknown, partition type is 0x8e


In my opinnion you should assign the right partition types to the partitions thanks to fdisk. This way you will begin to be able to mount them.

adrian15

---

### Post by gray-squirrel on 2007-03-22
> **rajan said:**
> 
according to this:
[http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds2/fsck.htm#HDRA10192CC1](http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/cmds/aixcmds2/fsck.htm#HDRA10192CC1)
you can run an fsck on an unmounted volume. i have heard [read] that there is possibly some problems running fsck on LVM, but its replacement, vgck, doesn't seem to do anything:

```

rajan@paravati:~$ sudo vgck /dev/hdb1
  Volume group "hdb1" not found
rajan@paravati:~$ sudo vgck /dev/hdb
  Volume group "hdb" not found

```

I was going to advise against using [FONT="Courier New"]fsck[/FONT] on the actual drive and use it on a drive image instead, but I was too busy since my last post here and you've already done it.  In any case, [FONT="Courier New"]vgck[/FONT] requires the LVM group name be specified, not the physical drive or partition name.

The only problem is that we need to recreate the LVM temporarily, just for the data recovery.  It is on one drive, right?  If so, that might be very easy to set up.

You said you didn't have the information to recreate the LVM, though.  Try [this method]("http://codeworks.gnomedia.com/archives/2005/general/lvm_recovery/") and see if it helps.  If this works, then we can run [FONT="Courier New"]ddrescue[/FONT] on that LVM (if there's space on the new drive).  You could try [FONT="Courier New"]vgck[/FONT] again, although I'm not sure how much of a bad condition the drive is in.

---

### Post by rajan on 2007-03-22
thanks a lot, gray-squirrel. I'm going to have a look at that after work today, but it looks like this might be a problem:

> Here is what I did: First find out the old UID’s of the partitions, this is in the /etc/lvm/backup/system file.

The problem is that I have tried to access the pieces of data that would have been on the / drive in my old disk, but I can never get to them. I think I could have simply recreated the /etc files if I could have accessed them (and I think they're the ones giving me problems), but I can't get to the data that I believe is on /dev/hdb5. 

at least i'll have something to do at work....:guitar:

---

### Post by gray-squirrel on 2007-03-22
I didn't realize until now that [FONT="Courier New"]hdb1[/FONT] was a boot partition.  ](*,)

---

### Post by rajan on 2007-03-23
ok, i just gave that method a shot, but the limiting step was that I didn't have a UID for my LVM. I tried this method:

[http://tldp.org/HOWTO/LVM-HOWTO/uuidfixer.html](http://tldp.org/HOWTO/LVM-HOWTO/uuidfixer.html)

but I think I have to be able to mount the volume before I can use that. right now it's really just curiosity that's keeping me at this. I would really really like to know how my system got so [insert favorite word here]-ed up. 

Not all is lost though...I recently learned that the company that most of my college buddies now work for is a company that does a lot of hard drive firmware/software and recovery software. so i guess they should be able to help :) 

thankfully i did make enough backups that I don't really need my data and if you would have asked me a few months ago if i would trade my data for all the insights i've gained about my system i would have taken that deal. thanks again please let me know if there are any more ideas. if i find out what went wrong/how to fix/avoid it, i'll repost here. 

-rajan

---

