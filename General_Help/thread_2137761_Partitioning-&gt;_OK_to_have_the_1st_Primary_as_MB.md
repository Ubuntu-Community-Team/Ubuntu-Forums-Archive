---
title: "Partitioning-&gt; OK to have the 1st Primary as MBR, Grub and (/) of primary OS?"
date: 2013-04-21
forum: General Help
---

### Post by mikodo on 2013-04-21
Hi everyone,

From man fdisk:

Linux  needs  at  least one partition, namely for its root file system.
       It can use swap files and/or swap partitions, but the latter  are  more
       efficient. So, usually one will want a second Linux partition dedicated
       as swap partition.  [B]On Intel compatible hardware, the BIOS  that  boots
       the  system can often only access the first 1024 cylinders of the disk.
       For this reason people with large disks often create a third partition,
       just  a  few  MB large, typically mounted on /boot, to store the kernel
       image and a few auxiliary files needed at boot time, so as to make sure
       that  this  stuff  is  accessible to the BIOS[/B].  There may be reasons of
       security, ease of administration and backup, or testing,  to  use  more
       than the minimum number of partitions.

My machine:

> $ sudo fdisk -l
   
```
/dev/sda1   *boot       1        2432    19530752   83  Linux
/dev/sda2            2432       38914   293038081    5  Extended
/dev/sda5            2432       22062   157677568   83  Linux
/dev/sda6           38184       38914     5859328   82  Linux swap / Solaris
/dev/sda7           22382       25047    21412109+  83  Linux
/dev/sda8           25049       27202    17301973+  83  Linux
/dev/sda9           27335       29926    20820208+  83  Linux
/dev/sda10          30076       32651    20691688+  83  Linux
/dev/sda11          32774       35384    20972826   83  Linux
/dev/sda12          35514       38060    20458746   83  Linux

```
QUESTION:

So, on my Intel machine my /dev/sda1 partition holds the MBR, Grub2, and the (/) partition of my primary install.  

 Would it be better, (with my new drive I am replacing the old one out with), to make a small first Primary Boot partition on the drive, as mentioned in man fdisk? 
Or, it is OK to continue with partitioning like I have now, for my Linux only installs?

Thanks.

;p

---

### Post by oldfred on 2013-04-22
Not sure that comment in fdisk is current. Drives have not used cylinders since they went over 8GB and converted to LBA - large block allocation. I do remember having to type into BIOS the CHS settings of drives back then.

There are old systems with BIOS that still have a 137GB boot limit. The entire / (root) or a boot partition must be inside the 137GB limit. The rest of the drive then can be /home or data.
There have been issues with some BIOS where something similar occurs. There was a bug in grub where very large / (root) partition over 500GB caused issues and something similar still appears. In those cases  a /boot still seems to be required, but we do not know before hand. Seems more common with external drives, perhaps a USB driver issue?

       Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

   First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by mikodo on 2013-04-22
Thanks oldfred.

A lot of interesting reading there written by some familiar "heavy hitters".

 I have an older gparted gui in Ubuntu Lucid, that is still my primary install, that shows a 1MiB unallocated slice (sector 2048) at the front of the drive, that is not seen in gparted in Xubuntu Precise's version. Now I understand why that is there. Why it reads differently in fdisk, I don't know. 

So, I am alright configuring the new drive similarly. 

;p

---

### Post by oldfred on 2013-04-22
Do not use old versions of gparted. Either use the live version on a new Ubuntu or download Parted Magic or gparted liveCD.

 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

I also boot many Ubuntu's across several drives. I prefer not to have a separate /home, but have data partitions that I mount in every install and use the same data in every install. Some do share /home but use different userIDs (UID) or attempt to share but usually some configuration will eventually overwrite one from another install.

---

### Post by mikodo on 2013-04-22
Thanks oldfred.

I will be making a separate data partition on next disk install.

I have decided on using Carla's setup proceedure here:

[http://www.linuxtoday.com/blog/2009/08/painless-linux.html](http://www.linuxtoday.com/blog/2009/08/painless-linux.html)

I will use your guide on how to symlink the data to installs. Post #5:

[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Thanks for the tip about using newer gparted or partedmagic live cd's.

;p

---

### Post by oldfred on 2013-04-22
I actually use Carla's little script, but I think that was a version with a typo. Your link is to an early version where I did it on line at a time. After several installs I converted that to a script, then figured out the typo in the one liner and now use that.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

    

Part of my mount new data partition in new install script. I create mounts, auto edit fstab, and link folders as one script.

```
# New install so folders are empty, just delete empty folders
rm -rf Documents/
rm -rf Downloads/
rm -rf Music/
rm -rf Pictures/
rm -rf Videos/

# auto link all folders:
#for i in `echo /usr/local/fred/data`;do ln -s $i; done 
# All folders to be linked in /home are in /data as folders
for i in `echo /mnt/data/*`;do ln -s $i; done
ln -s /mnt/shared

#old manual mount of each folder - see one line above
# Also changed default mount from /usr/local/fred/data to just /mnt/data
#This works: for i in `ls /usr/local/fred/data`;do echo $i; done
#for var in *.rar;do unrar xf "$var" /media/HDD/folder/$var/;done
#ln -s /usr/local/fred/data/Music
#ln -s /usr/local/fred/data/Documents
#ln -s /usr/local/fred/data/Downloads

```

---

### Post by oldfred on 2013-04-22
Do be careful with links.

I let new software create folders in /home and eventually copy data to my data partition and link it back manually.

I have accidentally not paid attention, think I had not copied data,  and copied a link back to the data partition which then overwrites the data structure. While data is technically there, the folder structure of that folder is gone. If not good backups, then you have to use photorec, which I did and it is a pain as it is slow and files do not have original names.

---

### Post by mikodo on 2013-04-22
> **oldfred said:**
> Do be careful with links.

I let new software create folders in /home and eventually copy data to my data partition and link it back manually.

I have accidentally not paid attention, think I had not copied data,  and copied a link back to the data partition which then overwrites the data structure. While data is technically there, the folder structure of that folder is gone. If not good backups, then you have to use photorec, which I did and it is a pain as it is slow and files do not have original names.
I have been reading more about this, including other people's suggestions, which all pretty much say the same as your guides, that I have found.

I am trying to learn enough about this before the deed, so as to be as informed as possible to enhance carefulness.

You have been very helpful.

Thanks.

;p

---

### Post by sgage on 2013-04-23
> So, on my Intel machine my /dev/sda1 partition holds the MBR, Grub2, and the (/) partition of my primary install. 

Just wanted to point out that /dev/sda1 does NOT hold the MBR. The MBR is not contained in any partition. Indeed, along with the initial bootstrap routine, it contains the partition table that defines the partitions on the drive.

---

### Post by mikodo on 2013-04-23
> **sgage said:**
> Just wanted to point out that /dev/sda1 does NOT hold the MBR. The MBR is not contained in any partition. Indeed, along with the initial bootstrap routine, it contains the partition table that defines the partitions on the drive.
I was questioning myself as I wrote, that the MBR was in the drive /dev/sda1. I was thinking I would be corrected pretty quickly if I was wrong by a geek reading my thread, but it took until now by you. I appreciate that. 

I got the idea, that the MBR was in /dev/sda1 from running ...
```
sudo fdisk -l                      
```
It shows /dev/sda1 *boot   (I *guess* it is referring to GRUB, or another *guess* is that it just signifies the drive (/dev/sda). I dunno really.

So, MBR is attached to drive(s).

Thank you.

;p

---

### Post by oldfred on 2013-04-23
In the MBR booting the system boots from BIOS which enumerates hardware onto drive and jumps to MBR. MBR has boot code and with Windows, lilo, syslinux, it reviews partition table and finds the partition with the boot flag. The partition with the boot flag has more boot code in the PBR or partition boot sector.
Grub does not use boot flag, but a few BIOS will not even let you start to boot without a boot flag, so we still suggest one on a primary partition.

       Multibooters, Pictures here worth 1000+ words - for quick review just review pictures.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

The new UEFI boot is a lot different than the old BIOS boot.

---

### Post by mikodo on 2013-04-24
Thanks Fred.

I was going blind and getting friggin' confused until I realized that I don't need to know how windows does things before and after vista. So, I started skipping stuff.

Basically, what I got out of this is this. ( I don't use windows, so most of that I glossed over ).

BIOS is in the motherboard (a chip) which starts the hardware  (CD/DVD/Floppy/Hard Drive) and passes off to the Master Boot Record  (MBR) in the initial part of the hard drive. Parts of the  MBR is  actually the boot program and the Partition Boot Record (PBR). The most  common name for the boot program part of the MBR is the Initial Program Loader  (IPL), which passes off to Grub2 which can be on the same initial part  of the drive or in any partition chosen. Grub2 can act independently as  or in conjunction with it's linux Program Boot Manager (PBR) to act as  the linux boot-manager and passes to the linux kernel to start the OS. I  am not saying any of this is correct just that, that is what I got out  of the page.

Whew. My Head Hurts!

Thanks.

EDIT: Oh ya, I forgot you already explained it. So never mind my stuff, lets just read yours. Duh!

;p

---

### Post by oldfred on 2013-04-24
If you really want to get confused.

Do not get me started on the new UEFI  as I barely understand that myself. It has been the Apple standard since they converted to Intel. And now Windows implemented UEFI with secure boot which makes it much more difficult to install dual boot.

---

