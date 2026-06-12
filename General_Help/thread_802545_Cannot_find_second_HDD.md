---
title: "Cannot find second HDD"
date: 2008-05-21
forum: General Help
---

### Post by Funky91 on 2008-05-21
Right, here's the problem.

I have built a PC out of spare parts for a friend and have installed xubuntu on it. When I first made it I had put one 6GB HDD in it. I have added another 6GB HDD since I have installed xubuntu.. The drive is recognized at boot and xubuntu recognizes it in gparted. However I cannot find the drive to mount it.

I have used gparted in xubuntu to format the second hard drive to ext3 so it works.

Please help or my friend will be stuck with 6GB!!!

---

### Post by phidia on 2008-05-21
Does sudo fdisk -l show the drive?
Once you know how the system ID's it you can mount it
with the mount command. 
For instance: sudo mount /dev/hdb /mnt/mydrive
BTW you can create any mount directory you want in /mnt or /tmp
You will probably want to check out how to edit fstab so you can auto mount the drive.

---

### Post by danwood76 on 2008-05-21
/tmp isnt a good place for mount points as its supposed for temporary hard storage.

use /mnt if you mant the drive to be mounted and semi hidden or /media if you want it in places and on your desktop.

to find the block device and partitions for the drive run:
```

sudo fdisk -l

```
if you havent created partitions on the drive use parted ;)

---

### Post by Funky91 on 2008-05-21
Yeah, it does, the output of sudo fdisk -l is

```
Disk /dev/hda: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a420a41

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         748     6008278+  83  Linux
/dev/hda2             749         788      321300    5  Extended
/dev/hda5             749         788      321268+  82  Linux swap / Solaris

Disk /dev/hdb: 6481 MB, 6481293312 bytes
255 heads, 63 sectors/track, 787 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37593758

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         787     6321546   83  Linux
Partition 1 has different physical/logical endings:
     phys=(785, 254, 63) logical=(786, 254, 63)

```

---

### Post by danwood76 on 2008-05-21
to mount that to /media/disk2 do:
```

sudo mkdir /media/disk2 # this makes the mountpoint
sudo mount -t ext3 /dev/hdb1 /media/disk2 # this does the mount

```

that should then appear on your desktop as disk2, replace disk2 in the two above instructions to whatever you want the mountpoint to be.

-- edit --

you can add this to you fstab to make it mount automatically on boot
(sudo gedit /etc/fstab)

```

/dev/hdb1 /media/disk2 ext3 defaults 0 1

```

---

### Post by Tyler H on 2008-05-21
I've got the same problem in 64bit Hardy. A spare IDE 80 gig (My main is a 120 SATA) will not show up.

It shows in boot and doesn't in Ubuntu, but when I run Gparted it shows up with warning of bad superblocks.

I've formated the drive in everyway and filetype I could think of with no luck.

---

### Post by danwood76 on 2008-05-21
It wont just show up under linux, you have to tell it to mount it (using fstab) to where you want it.
Its way more versitile this way ;)

---

### Post by Funky91 on 2008-05-21
OK, that seems to have made the mountpoint and mounted it but I can only access it by manually going into /media. how do I add that to the desktop and places menu?

also how can I get it to mount at startup. This would be good as my friend has no other linux experience so it would be a lot easier for him if he did not have to mount it manually.

---

### Post by Tyler H on 2008-05-21
Why does the answer always have to include CLI?? 
I tried fstab and it didn't work.

---

### Post by Funky91 on 2008-05-21
now that is odd...

just as it was going so well the display suddenly cut out and when I reset it nothing happened, the monitor wouldnt recognize it. 

tried another graphics card, same problem! hmmmmm

---

### Post by strabes on 2008-05-21
> **Tyler H said:**
> Why does the answer always have to include CLI?? 

Because it's easier to tell you to type in one command than to tell you to go to this screen, then click in the bottom left on a button, then scroll here, then check this box, then go to this other dialog box and change some option. Do not complain about the help you are receiving here. The people here are volunteers using their free time to help you.

Please paste the output of the following command. ```
cat /etc/fstab
```

By the way, simply pasting in the line to fstab and saving the file (as the root user) will not work. You either have to run "sudo mount -a" or restart your computer.

---

### Post by Tyler H on 2008-05-22
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f1901f73-2d59-4ced-b4ed-a7cd2ded3eb1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0440247f-5a74-4cb0-ba04-abfe67fd37a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
tyler@tyler-desktop:~$

---

### Post by Tyler H on 2008-05-22
Bump

---

### Post by dodgeman79 on 2008-05-23
whats your output of
```
sudo fdisk -l
```

---

### Post by Tyler H on 2008-05-26
Sda1 is the disk I'm after.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd80c4fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc61cc61c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1337    10739421   83  Linux
/dev/sdb2            1338       19457   145548900    5  Extended
/dev/sdb5           19089       19457     2963961   82  Linux swap / Solaris
/dev/sdb6            1338       19088   142584844+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 1042 MB, 1042153472 bytes
33 heads, 61 sectors/track, 1011 cylinders
Units = cylinders of 2013 * 512 = 1030656 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

---

### Post by danwood76 on 2008-05-27
Open up your fstab for editing:
```

sudo gedit /etc/fstab

```
add this line to the bottom:
```

/dev/sda1 /media/HD2 ext3 defaults 0 1

```
then create the mountpoint and mount it to check:
```

sudo mkdir /media/HD2
sudo mount -a

```
Change the HD2 in the above lines to whatever your want the disk to show up as on your desktop.

---

