---
title: "Resizing Partition"
date: 2013-08-31
forum: General Help
---

### Post by badruk on 2013-08-31
Hello I'd like to know if I'm still able to resize the partition I'm using with ubuntu or what am I supposed to do to resize it into 2 subpartition of 500 and 150 gb :)

This is my lsblk

```
davide@davide-desktop:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931,5G  0 disk 
&#9500;&#9472;sda1   8:1    0   350M  0 part 
&#9500;&#9472;sda2   8:2    0 253,6G  0 part 
&#9500;&#9472;sda3   8:3    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0 671,6G  0 part /
&#9492;&#9472;sda6   8:6    0     6G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  


```

The partition I'm talking about is the 671G to divde in 2 without affecting the one of 253 ( with nexus 8 installed on )

Also, in the case I should reinstall ubuntu and use gparted before the installation which type is best to work for both windows 8 and linux?

---

### Post by rai_shu2 on 2013-08-31
I think you'll want to:

```
df -h
```

Make sure you have enough Available space on sda5, first. Then run gparted from the LiveCD/USB.

> Also, in the case I should reinstall ubuntu and use gparted before the  installation which type is best to work for both windows 8 and linux?

Which type of what? And what do you mean by best?

---

### Post by ibjsb4 on 2013-08-31
This any help?

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

---

### Post by David_Pecot on 2013-08-31
Resizing sda5 won't affect the 253 Gb partition at all.  I use Gparted for such things.  Backups are always in order even though in reality I rarely have problems.

---

### Post by badruk on 2013-09-01
Ok so I wasn't able to resize the partition sda5 because I was actually using that, in order to I need to run linux from the live cd. Right? :)

By which kind is the best I mean which fyle system is best suitable to host datas for both Ubuntu and Windows 8 without making strange things ( as I was used to with ntfs and OSx ). Also I'd like to host, on that partition, files those are bigger than 4 Gb, so I'd dodge FAT32 :) Which is best for my purposes?

---

### Post by Quackers on 2013-09-01
Yes, run gparted from the live cd/usb desktop. It may take some time to run.
NTFS should be fine for shared data - at least it is on mine :-)

---

### Post by badruk on 2013-09-01
This is what I did, I'd like to have the free space outside of dev/sda3 in order to have it indipendent of the others ( to prevent future fails of mine while formatting or upgrading something )

How can I pull the unallocated space, that's in /dev/sda3 outside of it and make it able to host a new partition?

[http://imgur.com/xXGSr1t](http://imgur.com/xXGSr1t)

---

### Post by rai_shu2 on 2013-09-01
Actually, you need to keep sda3 the way it is and try not to worry about it. That's just how partitioning works.

At this point, you have 564.19 GiB of space, and you can use gparted to format whatever you want there.

---

### Post by Quackers on 2013-09-01
Just create a logical partition from the unallocated space within sda3 which is an extended partition (which is a container for logical partitions). Or more than one new logical partition from that unallocated space, if you want. Obviously the new partition(s) can not be primary partitions (so could not boot a Windows installation without other preparations) but they'd be fine for most Linux installations.

---

