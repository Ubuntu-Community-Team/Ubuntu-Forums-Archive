---
title: "weird extended Partition"
date: 2015-08-06
forum: General Help
---

### Post by mantazasas on 2015-08-06
Hello i have weird extended sda3 partition : 
[IMG]http://s27.postimg.org/5hxv77g4z/wtf.png[/IMG]
which in fact shouldn't be there because even without it my is filled with 692GB from 698GB
So i woondering maybe someone can explain how do i can delete this partition and why it are here?

---

### Post by TheFu on 2015-08-06
That is where linux is installed. If you delete it, Linux will be deleted.
Why is it this way?  There is too much history - read the wikipedia article on MBR disk partitioning.
[https://en.wikipedia.org/wiki/Master_boot_record](https://en.wikipedia.org/wiki/Master_boot_record)  Basically, it is a hack to get around the limit of 4 primary partitions in any MBR partition table.  If you need more than 4 partitions, then you'll need to be able to create "logical partitions" and those can only go inside an "extended partition".  I think there is some limit to the number of logical partitions - 128 perhaps?

These days I use GPT partitioning, but Windows has limitations on using that which do not matter to Linux. UEFI BIOS and 64-bit OS only. You might want to read the wikipedia article on GPT disk partitioning. [https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)  GPT allows all partitions to be "primary" - there is a limit, but it is NOT 4. You can look up the limit - it is over 100. I cannot think of a good reason it would be anything but 255 ... but don't recall now.

For a comparison: [http://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/](http://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/)

---

### Post by mantazasas on 2015-08-06
Thank you for reply but damn i'm now confused more than was i was.. 
I always taught thath linux is installed on /dev/sda6/ .

---

### Post by TheFu on 2015-08-06
> **mantazasas said:**
> Thank you for reply but damn i'm now confused more than was i was.. 
I always taught thath linux is installed on /dev/sda6/ .

a) think you saw my initial post before I was done. Please re-read.
b) sda6 is nothing special. Have a few linux systems here - doubt that any are installed on sda6.  Let's see:```

$ lsblk
NAME                            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                               8:0    0 119.2G  0 disk  
&#9500;&#9472;sda1                            8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                            8:2    0     1K  0 part  
&#9492;&#9472;sda5                            8:5    0   119G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)           252:0    0   119G  0 crypt 
    &#9500;&#9472;c720--vg-root (dm-1)      252:1    0  51.9G  0 lvm   /
    &#9500;&#9472;c720--vg-lv--swap (dm-2)  252:2    0   4.1G  0 lvm   [SWAP]
    &#9492;&#9472;c720--vg-lv--Stuff (dm-3) 252:3    0    50G  0 lvm   /mnt/stuff
```
Nope. That is a netbook - fully encrypted.

```
$ lsblk 
NAME                             MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                                8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1                             8:1    0   100M  0 part 
&#9500;&#9472;sda2                             8:2    0    60G  0 part 
&#9500;&#9472;sda3                             8:3    0  58.6G  0 part 
&#9500;&#9472;sda4                             8:4    0     1K  0 part 
&#9500;&#9472;sda5                             8:5    0  19.9G  0 part /
&#9500;&#9472;sda6                             8:6    0   6.4G  0 part [SWAP]
&#9492;&#9472;sda7                             8:7    0 786.6G  0 part 
  &#9500;&#9472;vg--hadar-lv--hadar (dm-0)   252:0    0 393.5G  0 lvm  /var
  &#9492;&#9472;vg--hadar-lv--backups (dm-1) 252:1    0   393G  0 lvm  /Backups
```
Nope. That's a VM server. / is on sda5 for some reason.

```
$ lsblk 
NAME                           MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                              8:0    0 298.1G  0 disk 
&#9492;&#9472;sda1                           8:1    0 298.1G  0 part 
  &#9492;&#9472;istar--stuff-lv--tv (dm-3) 252:3    0   150G  0 lvm  /TV
sdb                              8:16   0   1.8T  0 disk 
&#9492;&#9472;sdb1                           8:17   0   1.8T  0 part /misc/2TB
sdc                              8:32   0   3.7T  0 disk 
&#9500;&#9472;sdc1                           8:33   0     1M  0 part 
&#9500;&#9472;sdc2                           8:34   0   244M  0 part /boot
&#9492;&#9472;sdc3                           8:35   0   3.7T  0 part 
  &#9500;&#9472;istar--vg-root (dm-0)      252:0    0  52.3G  0 lvm  /
  &#9500;&#9472;istar--vg-swap_1 (dm-1)    252:1    0   3.6G  0 lvm  [SWAP]
  &#9492;&#9472;istar--vg-lv_media (dm-2)  252:2    0   3.5T  0 lvm  /D
sdd                              8:48   0   3.7T  0 disk 
&#9500;&#9472;sdd1                           8:49   0  58.6G  0 part 
&#9492;&#9472;sdd2                           8:50   0   3.6T  0 part 
```
Nope. That's a media server.
```

$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
vda    253:0    0  12.4G  0 disk 
&#9500;&#9472;vda1 253:1    0   7.2G  0 part /
&#9492;&#9472;vda2 253:2    0   2.3G  0 part /var/www
```
 Nope. That's a blog server.

```
$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
vda    253:0    0  19.4G  0 disk 
&#9500;&#9472;vda1 253:1    0  16.5G  0 part /
&#9492;&#9472;vda2 253:2    0     3G  0 part [SWAP]
```
Nope. That's my main desktop.

```

$ lsblk
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
mmcblk0     179:0    0 29.7G  0 disk 
&#9500;&#9472;mmcblk0p1 179:1    0  243M  0 part /boot
&#9492;&#9472;mmcblk0p2 179:2    0 29.5G  0 part /
```
Nope. That's a raspberry pi2 running Kodi (actually OSMC is the distro).

You get the point ...  I could post output for about 20 other systems. If any had linux on sda6, it would be a coincidence, nothing more.

BTW - I cannot read the text in that image. If you want more help, please post the output from **sudo parted -l**

---

### Post by yancek on 2015-08-06
> I always taught thath linux is installed on /dev/sda6/ .         

It is.  sda3 is an Extended partition which cannot contain data but is a method used to create additional partitions which are called logical partitions which can contain data.  Logical partitions in Linux always start with sda5 and in your case, sda5 is the swap partition.  Add the size of the swap and sda6 and you come out with the size of the Extended partition.  You can do an online search for Extended partitions and what it means.  Lots of explanations.

So there is nothing weird about your setup, that's exactly how it works.

---

### Post by grahammechanical on 2015-08-06
I built my machine myself. I do not have Windows on it. The machine has a BIOS boot system. So, I have the 4 primary partition limit. I have Ubuntu installed in the first primary partition and that is sda1. The second primary partition is an Extended partition and inside that I can create as many logical partitions as I need. I actually have a second installation on sda7 which is a Logical partition inside the Extended partition which is itself a special kind of Primary partition.

So, it is not true that Linux is always installed on sda6. That may be true for machines with Windows pre-installed. Especially if the 4 primary partitions have already been used. In that case at least one primary partition will have to be deleted and then a new primary partition created as an extended partition into which logical partitions can be created to be used by Linux. And so we may get to a situation with Ubuntu being on sda5 or sda6.

An encyclopedia is better at providing information on subjects like this than a user forum. What I know on this subject I learned by studying articles in computer journals and in encyclopedias.

Regards.

---

### Post by mantazasas on 2015-08-06
Well, thank you all  for help now it's much more clear :)

---

