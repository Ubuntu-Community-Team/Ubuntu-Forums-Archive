---
title: "Making the complete switch (from duel boot to just Linux)"
date: 2006-12-07
forum: General Help
---

### Post by raveneffct on 2006-12-07
Hi, I currently use duel boot and I was wondering if there is a way to get rid of Windows while keeping the Ubuntu I already have? Doing a complete switch and having Ubuntu taking all the space from the Windows paritions. Or will I have to wipe everything out and start with a fresh ubuntu? Thanks in advance.

I want to know incase I do decide to do a complete switch. Also, is there a way with duel boot that I can give almost everything (partition wise) to linux and leave windows with the bare minimum(while still keeping the files and applications I have on there).

---

### Post by charlie. on 2006-12-07
Use ubuntu's partitioning tools to destroy the Windows partition and replace it with an EXT3 or EXT2 partition, then mount that somewhere on your Linux drive. That will give your whole hard-drive to Linux.

Removing the partitions will not remove Windows from Grub's menu. To do that, go edit menu.lst in /boot/grub. If you've only got one opperating system, you can also drop your grub timeout to something really low. (You still need at least one second here in case you need to access the "recovery" options.)

---

### Post by Crooksey on 2006-12-07
You can, what you will need to do is:

1) Delete your XP partion(s) from ubuntu.
2) Make a new ext3 partion in that space.
3) Make the new partion your home partion
4) Add the new partion to your FSTAB

I wont tell you how to di it all, you learn alot more by researching the methods and understanding why, other than just copy and paste.

---

### Post by raveneffct on 2006-12-07
> **Crooksey said:**
> You can, what you will need to do is:

1) Delete your XP partion(s) from ubuntu.
2) Make a new ext3 partion in that space.
3) Make the new partion your home partion
4) Add the new partion to your FSTAB

I wont tell you how to di it all, you learn alot more by researching the methods and understanding why, other than just copy and paste.

Also, Is there a way (keeping duel boot) that I can give almost everything (partition wise) to linux and leave windows with the bare minimum(while still keeping the files and applications I have on there)

---

### Post by raveneffct on 2006-12-07
Does anyone have an answer to my second question, I would appreciate it. Thanks.

---

### Post by bernied on 2006-12-07
Sounds like you want to resize the windows partition, to make it smaller. This might be challenging if windows uses the ntfs filesystem. If you are resizing partitions, do it from a live cd, you don't want to be messing with partitions on a disk that you are using at the time. The applications you can use are gparted, qtparted, parted (and probably a few others), the last on that list is most likely to be available on a live cd, but is totally command line.

I don't think any of these will resize an ntfs partition (someone tell me if I'm wrong??), for that you might need somthing commercial, like partition-magic.

There is another, slightly more involved, way. But you'll need to do some work. Basically, you would copy the entire filesystem of the windows install, maybe using the 'tar' command, onto some spare space, then delete the windows partition, then create a new windows partition that is smaller, then format it as ntfs (this might be tricky, maybe use a windows recovery cd??), and copy the files back to it. There are plenty of ways that this could go wrong, so do some research (I take no responsibility).

Or you could delete the windows partition, create a new smaller one (easier if you make it FAT32, not ntfs), then reinstall windows on the new partition. This way you'd lose all you windows applications, data and updates etc.

Or buy a new hard-drive

---

### Post by raveneffct on 2006-12-07
> **bernied said:**
> Sounds like you want to resize the windows partition, to make it smaller. This might be challenging if windows uses the ntfs filesystem. If you are resizing partitions, do it from a live cd, you don't want to be messing with partitions on a disk that you are using at the time. The applications you can use are gparted, qtparted, parted (and probably a few others), the last on that list is most likely to be available on a live cd, but is totally command line.

I don't think any of these will resize an ntfs partition (someone tell me if I'm wrong??), for that you might need somthing commercial, like partition-magic.

There is another, slightly more involved, way. But you'll need to do some work. Basically, you would copy the entire filesystem of the windows install, maybe using the 'tar' command, onto some spare space, then delete the windows partition, then create a new windows partition that is smaller, then format it as ntfs (this might be tricky, maybe use a windows recovery cd??), and copy the files back to it. There are plenty of ways that this could go wrong, so do some research (I take no responsibility).

Or you could delete the windows partition, create a new smaller one (easier if you make it FAT32, not ntfs), then reinstall windows on the new partition. This way you'd lose all you windows applications, data and updates etc.

Or buy a new hard-drive

Is it possible to make my windows partition too small? Or will it stop me before im able to do that. And will making the partition smaller keep all my windows files or will it get rid of some? (new to linux, bare with me)

---

### Post by bernied on 2006-12-07
Generally the partition resizing applications will keep all the files and won't allow you to make the filesystem smaller than the files in it. However, windows will need a bit of space to run, so you might want to check independently, and decide beforehand how much space you want to give windows. If you post the output to 'sudo fdisk -l' and work out how much space windows is using now (maybe easiest to do this from windows), then maybe folk here will offer suggestions.

---

### Post by raveneffct on 2006-12-07
> **bernied said:**
> Generally the partition resizing applications will keep all the files and won't allow you to make the filesystem smaller than the files in it. However, windows will need a bit of space to run, so you might want to check independently, and decide beforehand how much space you want to give windows. If you post the output to 'sudo fdisk -l' and work out how much space windows is using now (maybe easiest to do this from windows), then maybe folk here will offer suggestions.


```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        7837    62894475    7  HPFS/NTFS
/dev/sda3            9057        9725     5373742+  db  CP/M / CTOS / ...
/dev/sda4            7838        9056     9791617+   5  Extended
/dev/sda5   *        7838        9002     9357831   83  Linux
/dev/sda6            9003        9056      433723+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by bernied on 2006-12-07
hmmmm, so this is not too easy for you. you have an 80gb disk, most of which is taken up by Windows, which looks like it might be using 3 primary partitions (1, 2 and 3), of which the main one is ntfs. Primary partition 4 is strangely out of order (it is located between 2 and 3) and is an extended partition, containing two logical partitions, which you have installed linux in. 

It looks like gparted can resize ntfs. Have a look here:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
You might find that gparted is included on your ubuntu live cd (??)

I'd suggest you try to shrink the ntfs partition (2) - use windows explorer to find out how much space is actually used on C: in windows and shrink to something a bit more than that - then grow the extended partition (4) to fill the space that's been made available, then grow the main ubuntu partition (5), or create a new partition(s) in the empty space inside the extended partition.

---

### Post by raveneffct on 2006-12-07
> **bernied said:**
> hmmmm, so this is not too easy for you. you have an 80gb disk, most of which is taken up by Windows, which looks like it might be using 3 primary partitions (1, 2 and 3), of which the main one is ntfs. Primary partition 4 is strangely out of order (it is located between 2 and 3) and is an extended partition, containing two logical partitions, which you have installed linux in. 

It looks like gparted can resize ntfs. Have a look here:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
You might find that gparted is included on your ubuntu live cd (??)

I'd suggest you try to shrink the ntfs partition (2) - use windows explorer to find out how much space is actually used on C: in windows and shrink to something a bit more than that - then grow the extended partition (4) to fill the space that's been made available, then grow the main ubuntu partition (5), or create a new partition(s) in the empty space inside the extended partition.

Wow, this partition stuff is CONFUSING. My head is spinning:confused: Which and where is the extended partition, and how do I know that it is said extended partition? ](*,)

---

### Post by raul_ on 2006-12-07
When i want to do that i use Partition Magic 8.0 in Windows. Works painlessly. My Windows partition gets smaller everyday

---

### Post by bernied on 2006-12-07
All the information is in your output from fdisk:
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        7837    62894475    7  HPFS/NTFS
/dev/sda3            9057        9725     5373742+  db  CP/M / CTOS / ...
/dev/sda4            7838        9056     9791617+   5  Extended
/dev/sda5   *        7838        9002     9357831   83  Linux
/dev/sda6            9003        9056      433723+  82  Linux swap / Solaris

Partition table entries are not in disk order
```That word extended at the end of the line for sda4 is the key, and the start and end block numbers tell you where it is relative to the other partitions. You can see by their start and end block numbers that sda5 and sda6 are INSIDE sda4. These two are logical partitions. The basic design of disk partitioning used on PCs allows only 4 primary partitions, using extended and logical partitions circumvents this limitation.

Yes it is complicated. Maybe reading this might help:
[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))
Even more detail here:
[http://www.ranish.com/part/primer.htm](http://www.ranish.com/part/primer.htm)

In your machine, if your disk was like a piece of magnetic tape (which is basically how the operating systems treat it) it would have its partitions organised something like this:

Start--Master Boot Record--Dell Utility (sda1, blocks 1-7)--Windows partition (sda2, blocks 8-7837)--Extended partition (sda4, blocks 7838-9056), which contains--Linux partition (sda5, blocks 7838-9002)--Linux swap partition (sda6, blocks 9003-9056)--(end extended partition)--Unknown (to me) partition, probably Windows stuff (sda3, blocks 9057-9725)

---

### Post by raveneffct on 2006-12-07
So what do you think is the most ideal partition setup for my computer. Like, what you said about the ordering being wrong..how do I fix this?

---

### Post by bernied on 2006-12-07
You don't need to 'fix' the ordering, if it were mine I wouldn't touch it. The thing is, we don't know much about those two extra partitions (1 and 3), and messing with those is almost guaranteed to kill windows. So leave those two alone, and maybe try what I said before:
> I'd suggest you try to shrink the ntfs partition (2) - use windows explorer to find out how much space is actually used on C: in windows and shrink to something a bit more than that - then grow the extended partition (4) to fill the space that's been made available, then grow the main ubuntu partition (5), or create a new partition(s) in the empty space inside the extended partition.Just beware that we don't really know enough to guarantee that this will be safe for the Windows install. Worst case scenario for you is that you lose Windows and have to start from a blank disk. So back up and be ready.

I think your easiest solution is a new hard disk. But it's not free.

---

### Post by Makurosu on 2006-12-07
> **bernied said:**
> hmmmm, so this is not too easy for you. you have an 80gb disk, most of which is taken up by Windows, which looks like it might be using 3 primary partitions (1, 2 and 3), of which the main one is ntfs. Primary partition 4 is strangely out of order (it is located between 2 and 3) and is an extended partition, containing two logical partitions, which you have installed linux in. 

It looks like gparted can resize ntfs. Have a look here:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
You might find that gparted is included on your ubuntu live cd (??)

I'd suggest you try to shrink the ntfs partition (2) - use windows explorer to find out how much space is actually used on C: in windows and shrink to something a bit more than that - then grow the extended partition (4) to fill the space that's been made available, then grow the main ubuntu partition (5), or create a new partition(s) in the empty space inside the extended partition.

I used the gparted live cd to shrink my Windows ntfs partition and make room for a 30gb ext3 partition for Ubuntu.  I also have an 80gb hard drive, and it worked perfectly.  I didn't even have to defrag my ntfs partition beforehand, because gparted took care of everything.  It is really slick and I highly recommend it, though be warned that it takes several hours with you looking on biting your nails.  Use the gparted live cd though.  I don't know what's on the Ubuntu live cd, but gparted's is all set up to do just that.

If I was going to delete my Windows partition, and I do have that thought from time to time, I would use the gparted live cd to delete the ntfs partition and expand the ext3 Ubuntu partition to fill the space.  It seems like kind of a waste though, because I have all my files on an external usb hard drive and 30gb is more than I'll ever need for Ubuntu.  I don't think I'm even using 10gb yet.  I have genealogy software on Windows that I have not found an adequate replacement for on Linux (Gramps screws up my Notes areas), so I'm going to need my Windows partition for awhile yet until that happens.

Best wishes to you, and try the gparted live cd. ;)

---

