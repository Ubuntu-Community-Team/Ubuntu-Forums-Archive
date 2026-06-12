---
title: "/home partition getting full - how to grow?"
date: 2013-01-03
forum: General Help
---

### Post by MichaelGld on 2013-01-03
My /home partition is 84% full, so I am looking for a way to increase the size of it without wiping my drive and starting over. I have attached a screenshot of my Gparted window. I have sda7 right next to it, and it's '/'.  I'd like to use a big hunk of that partition and add it to /home.

If someone would be kind enough to point me in the right direction, like to a tutorial I'd be grateful.

---

### Post by oldfred on 2013-01-03
Your hard drive looks full.

Windows really works best if the NTFS partition has 30% free and at 10% free is noticeably slow and may take forever for a simple defrag.
Linux likes extra room, and even hides 5% so you do not use too much, but once drive is as full as yours is, you need to plan on another drive or a larger drive.

---

### Post by tartalo on 2013-01-03
1. boot from live cd
2. reduce sda7 and move it to the right 
3. make sda6 bigger

BTW, you have plenty of things in sda7, do you need it all? perhaps you can make some room there before (by uninstalling packages, cleaning /var and so on. bleachbit can help if you don't know were to start).

Edit: Baobab is another useful tool in these cases.

---

### Post by Wim Sturkenboom on 2013-01-04
How do you get 200GB in the root partition :confused:

Are you running a server with massive mysql databases and massive websites? If so, throw in a new disk (or two or three or ...); I assume it would be the best in any case because you will probably run out of space again soon if you take some space from the root partition.

---

### Post by fdrake on 2013-01-04
> **MichaelGld said:**
> My /home partition is 84% full, so I am looking for a way to increase the size of it without wiping my drive and starting over. I have attached a screenshot of my Gparted window. I have sda7 right next to it, and it's '/'.  I'd like to use a big hunk of that partition and add it to /home.

If someone would be kind enough to point me in the right direction, like to a tutorial I'd be grateful.

cheapest/fastest way:
well if you have an external hhd partition it in ext3/4 and mount it in /home. (add the conf to the fstab . try to use UUID)
you can mount more then one disk into the same mountpoint.

---

### Post by rnerwein on 2013-01-04
> **MichaelGld said:**
> My /home partition is 84% full, so I am looking for a way to increase the size of it without wiping my drive and starting over. I have attached a screenshot of my Gparted window. I have sda7 right next to it, and it's '/'.  I'd like to use a big hunk of that partition and add it to /home.

If someone would be kind enough to point me in the right direction, like to a tutorial I'd be grateful.
hi
for emergency you can use the command tune2fs to get rid of the reserved blocks.
on the other side - what's the hell you stored in the root filesystem ( / ). normaly this is
not the place for music or games and so on.
cheers

---

### Post by MichaelGld on 2013-01-04
> **tartalo said:**
> 1. boot from live cd
2. reduce sda7 and move it to the right 
3. make sda6 bigger

BTW, you have plenty of things in sda7, do you need it all? perhaps you can make some room there before (by uninstalling packages, cleaning /var and so on. bleachbit can help if you don't know were to start).

Edit: Baobab is another useful tool in these cases.

Can I do that with gparted?

---

### Post by MichaelGld on 2013-01-04
> **Wim Sturkenboom said:**
> How do you get 200GB in the root partition :confused:

Are you running a server with massive mysql databases and massive websites? If so, throw in a new disk (or two or three or ...); I assume it would be the best in any case because you will probably run out of space again soon if you take some space from the root partition.

No, not running a server, just made a mistake when setting up the hard drive. What size would you recommend for root?

---

### Post by Wim Sturkenboom on 2013-01-04
> **MichaelGld said:**
> No, not running a server, just made a mistake when setting up the hard drive. What size would you recommend for root?
But it has 200GB of data in it. What is in there?

To answer about the the size of the root partition, 25GB should be sufficient and 50GB should be plenty. My install currently has 6GB used on the root partition; I do not install too much software though (2 tux games, virtualbox and some command line applications if I recall correctly).

---

### Post by MichaelGld on 2013-01-04
> **Wim Sturkenboom said:**
> But it has 200GB of data in it. What is in there?

To answer about the the size of the root partition, 25GB should be sufficient and 50GB should be plenty. My install currently has 6GB used on the root partition; I do not install too much software though (2 tux games, virtualbox and some command line applications if I recall correctly).

Holy crap! I've got a ton of files in there and I don't know why! It looks like some of them are duplicates of files and folders from my /home partition. Can you tell me what files and folders should normally be found in root?   I guess I'll spend the next days going through them and deleting them as needed.

Okay, this is weird: I opened two Nautilus windows, one sudo nautilus /, the other as /home. When I navigated to the "extra" home folder in root and deleted a duplicate empty folder, the other window opened to home changed and the second copy of the folder disappeared! It's like they are linked, or I don't know what the heck I am doing.

---

### Post by Wim Sturkenboom on 2013-01-04
> **MichaelGld said:**
> Holy crap! I've got a ton of files in there and I don't know why! It looks like some of them are duplicates of files and folders from my /home partition. Can you tell me what files and folders should normally be found in root?   I guess I'll spend the next days going through them and deleting them as needed.
:twisted:

To add to the list of installed SW (so you have an idea): skype and evolution.

---

### Post by MichaelGld on 2013-01-04
> **Wim Sturkenboom said:**
> :twisted:

To add to the list of installed SW (so you have an idea): skype and evolution.

I don't understand.

---

### Post by MichaelGld on 2013-01-04
> **rnerwein said:**
> hi
for emergency you can use the command tune2fs to get rid of the reserved blocks.
on the other side - what's the hell you stored in the root filesystem ( / ). normaly this is
not the place for music or games and so on.
cheers

Part of what's stored in root, I found, is a mirrored copy of what's in /home! I don't know how that happened. When I delete a file or folder from one, the other file/folder gets deleted as well. I don't remember setting up any symlinks so I have no idea how this happened.  Can anyone tell me how to undo this?

---

### Post by rnerwein on 2013-01-04
> **Wim Sturkenboom said:**
> But it has 200GB of data in it. What is in there?

To answer about the the size of the root partition, 25GB should be sufficient and 50GB should be plenty. My install currently has 6GB used on the root partition; I do not install too much software though (2 tux games, virtualbox and some command line applications if I recall correctly).
hi
for Wim --> your root is very small. don't forget /var/log if there is a daemon out of control your / will be filled up very fast and you can get problems with "login".
just a hint
cheers

for the other problem:
it would be nice to post an output of: sudo fdisk -l and df -k
cheers

---

### Post by grahammechanical on 2013-01-04
Can I have a guess?

Apart from the fact that I am seeing the picture as a reversed image. I would say that originally sda6 was the intended / (root) partition with sda7 the intended /home partition. And at some point (perhaps a re-install) the partitions have been reversed. And you are now using sda7 as the storage partition when it is officially the root partition.

You may need to think about saving all your important data and doing a fresh install with sda6 mounted as / and sda7 mounted as /home but with both partitions marked for format.

I occurs to me that you could install Ubuntu into sda6 with a mount point of / and a format but only give sda7 a mount point of /home and no format. Then you will not loose the data in sda7. You will need to clear out any system folders and files that are in there. I do not know how successful this will be.

Regards.

---

### Post by MichaelGld on 2013-01-04
> **rnerwein said:**
> hi
for Wim --> your root is very small. don't forget /var/log if there is a daemon out of control your / will be filled up very fast and you can get problems with "login".
just a hint
cheers

for the other problem:
it would be nice to post an output of: sudo fdisk -l and df -k
cheers
```

michael@michael-desktop:~$ sudo fdisk -l
[sudo] password for michael: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022322

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2000895      999424   83  Linux
/dev/sda2         2002942   568330239   283163649    5  Extended
/dev/sda3       568330240   976773119   204221440    7  HPFS/NTFS/exFAT
/dev/sda5         2002944    19578879     8787968   82  Linux swap / Solaris
/dev/sda6        19580928    80048127    30233600   83  Linux
/dev/sda7        80050176   568330239   244140032   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8235e066

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   369663999   184728576    7  HPFS/NTFS/exFAT
/dev/sdb3       369664000   371711999     1024000    7  HPFS/NTFS/exFAT
/dev/sdb4       371712000   976771071   302529536    f  W95 Ext'd (LBA)
/dev/sdb5       371714048   976771071   302528512    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa5b8c8f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63  1953520064   976760001    7  HPFS/NTFS/exFAT
``````
michael@michael-desktop:~$ df -k
df: `/root/.gvfs': Permission denied
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda7      240308744 203199140  24902604  90% /
udev             4036088         4   4036084   1% /dev
tmpfs            1617956      1204   1616752   1% /run
none                5120         0      5120   0% /run/lock
none             4044888       160   4044728   1% /run/shm
/dev/sda1         983704     64004    869732   7% /boot
/dev/sda6       29758532  23549232   4697620  84% /home
/dev/sr0          698970    698970         0 100% /media/Jazz_26
/dev/sdc1      976760000 962015024  14744976  99% /media/ProDrive
/dev/sdb5      302528508 166224104 136304404  55% /media/New DOWNLOADS
/dev/sdb3        1023996    682852    341144  67% /media/New DATA
/dev/sdb2      184728572  46742644 137985928  26% /media/A4AA13CAAA1397BE
```

---

### Post by Wim Sturkenboom on 2013-01-04
> **MichaelGld said:**
> I don't understand.
I showed the additional software that is installed (in the 6GB)

---

### Post by Wim Sturkenboom on 2013-01-04
> **rnerwein said:**
> 
for Wim --> your root is very small. don't forget /var/log if there is a daemon out of control your / will be filled up very fast and you can get problems with "login".
just a hint
cheers

I did not say that my root is 6GB ;) Only that my root partition is currently filled for 6GB.

And I'm running a netbook with 8GB HD space in total; no partitioning except for a little swap. But that runs Crunchbang instead of a resource heavy distro.

---

### Post by MichaelGld on 2013-01-04
> **Wim Sturkenboom said:**
> I showed the additional software that is installed (in the 6GB)

What 6 GB are you referring to?

---

### Post by MichaelGld on 2013-01-04
> **grahammechanical said:**
> Can I have a guess?

Apart from the fact that I am seeing the picture as a reversed image. I would say that originally sda6 was the intended / (root) partition with sda7 the intended /home partition. And at some point (perhaps a re-install) the partitions have been reversed. And you are now using sda7 as the storage partition when it is officially the root partition.

You may need to think about saving all your important data and doing a fresh install with sda6 mounted as / and sda7 mounted as /home but with both partitions marked for format.

I occurs to me that you could install Ubuntu into sda6 with a mount point of / and a format but only give sda7 a mount point of /home and no format. Then you will not loose the data in sda7. You will need to clear out any system folders and files that are in there. I do not know how successful this will be.

Regards.

I think you are right, I got the partitions switched. I remember I did a reinstall because Ubuntu would no longer get me to the desktop (turned out to be caused by a flaky DVD drive). Then I got the black screen hell because the nVidia drivers that worked fine in 11.10 were death to 12.04.

But if I could turn off the linkage between the two partitions, I could clean sda7 out, then expand sda6 during a live cd session.

---

### Post by Wim Sturkenboom on 2013-01-05
> **MichaelGld said:**
> What 6 GB are you referring to?
The space that my install currently takes. In post #9 I mentioned some additional SW that I installed and in post #11 two other applications.

It was just to show you that a 25GB root partition should be big enough for normal users.

---

