---
title: "messed up partitions please help"
date: 2006-12-21
forum: General Help
---

### Post by pjman on 2006-12-21
Please help...

My laptop is setup as dual boot. I was in Ubuntu trying to setup a GParted LiveUSB following the directions at [http://gparted.sf.net/liveusb.php](http://gparted.sf.net/liveusb.php). I was stupid enough to actually copy and past the command "syslinux -s /dev/sda1" without reading further (it should have been sdb1). Needless to say I messed up my machine and now I can't get grub to come up to allow me to choose the OS I want to boot to. Please, someone tell me this is reversible. 

Thanks in advance.

---

### Post by tagra123 on 2006-12-22
> **pjman said:**
> Please help...

My laptop is setup as dual boot. I was in Ubuntu trying to setup a GParted LiveUSB following the directions at [http://gparted.sf.net/liveusb.php](http://gparted.sf.net/liveusb.php). I was stupid enough to actually copy and past the command "syslinux -s /dev/sda1" without reading further (it should have been sdb1). Needless to say I messed up my machine and now I can't get grub to come up to allow me to choose the OS I want to boot to. Please, someone tell me this is reversible. 

Thanks in advance.

This may help you.

[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by pjman on 2006-12-22
Is grub restore an option on the Ubuntu live CD?

---

### Post by tagra123 on 2006-12-22
> **pjman said:**
> Is grub restore an option on the Ubuntu live CD?


Once the live cd is up and running go to a terminal

menu:  Applications-Accessories-Terminal

then type 

either 

grub

or

sudo grub

and follow the first set of instructions on the pag listed above.

Grub has it's own set of commands which are explained in the listing above.

If your ubuntu files are still there grub should find them.

---

### Post by pjman on 2006-12-22
```
setup (sda0)
```
gives me
```
Error 23: Error while parsing number
```

```
find /boot/grub/stage1
```
gives me
```
Error 15: File not found
```

I tried running fsck.ext3 on /dev/sda0-6 but ever time I got 

```
fsck.ext3: No such file or directory while trying to open /dev/sda[#]

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I don't know about running "e2fsch -b 8193"; should I?

I attached a picture of what GParted shows me. The system sees my hard drive as one big FAT32 drive. It was not formated. The command I ran "syslinux -s /dev/sda1" only took a second to run so maybe there is still hope...?

---

### Post by tagra123 on 2006-12-22
> **pjman said:**
> ```
setup (sda0)
```
gives me
```
Error 23: Error while parsing number
```

```
find /boot/grub/stage1
```
gives me
```
Error 15: File not found
```

I tried running fsck.ext3 on /dev/sda0-6 but ever time I got 

```
fsck.ext3: No such file or directory while trying to open /dev/sda[#]

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I don't know about running "e2fsch -b 8193"; should I?

I attached a picture of what GParted shows me. The system sees my hard drive as one big FAT32 drive. It was not formated. The command I ran "syslinux -s /dev/sda1" only took a second to run so maybe there is still hope...?


try running gparted from the livecd.  It will let you see what your hard drive currently look like.

I think you can also run plain ole parted (not graphical) and then use the command print at the command prompt.

Using gparted you can tell if the disk still has data on it. It will also let ou see the structure of your disk(s)

If the partitions are not empty then you are most likely just trying to get grub to find your installation. Are you 100% positive sda is the drive that the installation is on.

One in grub you can press tab to show options ???

look at this page

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

especially  this post 
ghostintheshell     September 22nd, 2005, 10:12 PM

---

### Post by bodhi.zazen on 2006-12-22
> **pjman said:**
> ```
setup (sda0)
```
gives me
```
Error 23: Error while parsing number
```

```
find /boot/grub/stage1
```
gives me
```
Error 15: File not found
```

To setup grub you must use grub speak:

```
sudo grub
root (hd0,5)
setup (hd0)
quit
```
Where (hdx,y) is your root partition.

The fact you have sd.... in Linux does not affect grub speak :)

Also, you will get > Error 15: File not found if you do not run grub as root.

Try```
sudo grub
```

---

### Post by tagra123 on 2006-12-22
I didnt see you picture the first time.

sda appeas to have 1 partition formated in fat32. Is this correct?

sda doesn't have anything on it. Are you sure this is your internal drive or is this a usb drive?

Click the arrows at the top right where sda is to see if there are any other drives

---

### Post by pjman on 2006-12-22
> **tagra123 said:**
> try running gparted from the livecd.  It will let you see what your hard drive currently look like.

A picture is attached to my last message

> **tagra123 said:**
> 
Using gparted you can tell if the disk still has data on it. It will also let ou see the structure of your disk(s)

If the partitions are not empty then you are most likely just trying to get grub to find your installation.

Please see attached picture. It looks like my partition table is screwed up. GParted see my drive as one big FAT32 partition. Before I ran the syslinux command that got be into this mess I had three primary partitions for windows and one extended partion with space for / and a small chunk of space for swap. 

> **tagra123 said:**
> 
Are you 100% positive sda is the drive that the installation is on.


Yes, I only have one hard drive in my laptop. That's what GParted is showing and sudo fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$
```


> **tagra123 said:**
> One in grub you can press tab to show options ???

Yes it does show me option when I press tab.

> **tagra123 said:**
> 
look at this page

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

especially  this post 
ghostintheshell     September 22nd, 2005, 10:12 PM

I followed the instructions but I cannot mount it. I think this is because my partition table is messed up. Is there any way of fixing it? Is there a "check disk" tool that might help?

> **bodhi.zazen said:**
> To setup grub you must use grub speak:

```
sudo grub
root (hd0,5)
setup (hd0)
quit
```
Where (hdx,y) is your root partition.

The fact you have sd.... in Linux does not affect grub speak :)

Also, you will get  if you do not run grub as root.

Try```
sudo grub
```

Tried root (hd0,#) with no luck. I still get the error with "find" even though I start grub with sudo.

Thanks again for any suggestions!!!

---

### Post by pjman on 2006-12-22
> **tagra123 said:**
> I didnt see you picture the first time.

sda appeas to have 1 partition formated in fat32. Is this correct?

"syslinux -s /dev/sda1" did that... I don't think the drive was actually formatted though, The [instructions to install GPartedLiveUSB]("http://gparted.sf.net/liveusb.php") say to copy the files over to the USB drive before running the syslinux command. I think syslinux just modifies how the drive can be booted..? Anyone know more about this command?

> **tagra123 said:**
> 
sda doesn't have anything on it. Are you sure this is your internal drive or is this a usb drive?

Click the arrows at the top right where sda is to see if there are any other drives

It's my hard drive. The USB stick only has 128MB and it's unplugged. I've rebooted multiple times and I'm now at work hoping to get this fixed so I can actually get some work done [-o<

---

### Post by sharkzf6 on 2006-12-22
If your Windows partition is still intact you can recover it. There is no harm done if you make a mistake overwriting Windows MBR with a Linux (or another system’s) boot loader because you always can restore the Windows MBR either by a Windows installation CD (anyone from Win2k or XP) or a Freedos CD downloadable from the Internet.
With the former you boot up the installation CD and wait until you can press R to opt for the Recovery Console where you just type

fixmbr
exit

The Freedos offers a CD ios image which you can burn and boot up the Dos 7.1 system. You can then use its fdisk.exe program 

fdisk /mbr

Either method will get your Windows MBR back. If you have access to a bootable floppy, the Windows MBR can also be restored using the command identical to the Freedos CD.

Good luck!

---

### Post by tagra123 on 2006-12-22
If you had more than 1 partition on this drive they appear to be gone.


I just googled and found this. There is a free download and it says it can restore deleted partitions.

Please post results if it works.

[http://www.softpedia.com/reviews/windows/Paragon-Partition-Manager-Professional-Review-42425.shtml](http://www.softpedia.com/reviews/windows/Paragon-Partition-Manager-Professional-Review-42425.shtml)

It looks like more than the MBR is missing.


To late for this time but to save you grief in the future, before running dangerous command that will change the partitions like this in the future

These two commands can save a lot of frustrations.

#BACKUP MBR and PARTITION TABLE
dd if=/dev/hdc of=/path/savedto/MBR-WITH-PARTTABLE-BACKUPDATE count=1 bs=512

#RESTORE
dd  if=/path/savedto/MBR-WITH-PARTTABLE-BACKUPDATE of=/dev/hdc count=1 bs=512


#BACKUP MBR
dd if=dev/hdc of=/path/to/save/to/MBR-BACKUPDATE count=1 bs=446

#RESTORE
dd if=/path/to/save/to/MBR-BACKUPDATE of=/dev/hdc count=1 bs=446

Both those files could fit on a floppy and can put your MBR and partition back in order quickly.

Read about them before simply copying the above lines.

---

### Post by sharkzf6 on 2006-12-22
> **tagra123 said:**
> If you had more than 1 partition on this drive they appear to be gone.


I just googled and found this. There is a free download and it says it can restore deleted partitions.

Please post results if it works.

[http://www.softpedia.com/reviews/windows/Paragon-Partition-Manager-Professional-Review-42425.shtml](http://www.softpedia.com/reviews/windows/Paragon-Partition-Manager-Professional-Review-42425.shtml)

BTW – I agree with this assessment. Unfortunately it appears that your partitions are fudged. It is possible, however, that using a Windows/DOS utility will unveil the partitions if they are actually still there. In that case, see my first post to recover your Windows. At least that way you’ll be able to use the computer, all be it with an inferior OS…   ;)

---

### Post by pjman on 2006-12-22
> **sharkzf6 said:**
> If your Windows partition is still intact you can recover it.

Using a Windows XP CD, Windows Recovery Console (or even the installer) doesn't recognize my hard drive... This is a HP NC6400 laptop. I think it has a SATA drive in it. I downloaded Freedos and ran fdisk /mbr. Now when I boot up my machine it says No active partition. In Fdisk there are no paritions. 

I'm guessing if I try to manually create a parition it will want to format it which is bad. ](*,) 

Should I give up hope now and try to just recover data using a data recovery tool? That's going to get messy, extracting RAW data, yuck!! :-&

---

### Post by pjman on 2006-12-22
> **tagra123 said:**
> 
I just googled and found this. There is a free download and it says it can restore deleted partitions.

Please post results if it works.

[http://www.softpedia.com/reviews/windows/Paragon-Partition-Manager-Professional-Review-42425.shtml](http://www.softpedia.com/reviews/windows/Paragon-Partition-Manager-Professional-Review-42425.shtml)

It looks like more than the MBR is missing.

The download is a demo. The boot disk it created found some of my partitions :-) Unfortunately the demo doesn't undelete partitions. I haven't decided if I'm going to buy it or not... If I do and if I have success I'll definitely post it here. Thanks for the BACKUP MBR and PARTITION TABLE commands. I'll be using that in the future.

If anyone knows of a free partition undelete tool please let me know.

Thanks!

---

### Post by bodhi.zazen on 2006-12-22
fdisk works just fine in this regard,

HOWEVER you MUST NOT have formatted the partition AND you must recreate the exact geometry (size and location of the partition).

You can try it: 

sudo fdisk /dev/hda

or what have you ...

---

### Post by pjman on 2006-12-22
> **bodhi.zazen said:**
> fdisk works just fine in this regard,

HOWEVER you MUST NOT have formatted the partition AND you must recreate the exact geometry (size and location of the partition).

You can try it: 

sudo fdisk /dev/hda

or what have you ...

Great idea :-) My luck has it, my work sets up these laptops with ghost images. I was able to look at two other exact laptops and get the file size in bytes for the three default partitions:

C:
12,587,548,672
D:
46,905,380,864
E:
526,413,824

When I installed Ubuntu I took 7GB off the end of the second partition and created an extended partition. But this shouldn't matter at least to get my first partition work...(I think/hope)?

Using the [Bit Calculator]("http://www.matisse.net/bitcalc/") I converted the bytes to kilobytes. In fdisk I created three new primary partitions. When asked for each size I put in:

```
/dev/sda1
+12292528K
/dev/sda2
+45806036K
/dev/sda3
+514076K
```

I then tried mounting /dev/sda1 with no luck:


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1531    12297726   83  Linux
/dev/sda2            1532        7235    45817380   83  Linux
/dev/sda3            7236        7297      498015   83  Linux
ubuntu@ubuntu:~$ sudo mkdir /mnt/windows
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/windows/ -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Now when I try to boot my machine from the hard drive I get the following error

```
Partition Signature !=55AA
```

Any other ideas? I feel like I'm so close...

---

### Post by bodhi.zazen on 2006-12-22
It looks like it did not quite work ....

Since you have mirrored drives, however, boot another laptop with the ubuntu desktop CD and get your partition table from fdisk (on a mirrored drive) rather then a calculation....

Also all your partitions are listed as Linux. Tell Fdisk the type of partition (ntfs, fat, etc)...

Good luck :)

---

### Post by tagra123 on 2006-12-22
A quick note from another post I made about how to backup and restore partitions.

It's worth the reading.!!!

[http://www.ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://www.ubuntuforums.org/showpost.php?p=1917499&postcount=40)

---

