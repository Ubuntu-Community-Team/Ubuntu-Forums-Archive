---
title: "Questions About Moving Partitions"
date: 2007-01-26
forum: General Help
---

### Post by kwilliam on 2007-01-26
I am planning on replacing one of my hard drives with a larger one, but I have a few questions. (I don't really know much about partitions and booting. The most I've ever done is make a FAT32 partition to share data between Linux and Windows.)

Here is my current setup. See the attached PNG screenshot of Gnome Partition Editor.

/dev/hda1 is Kubuntu, my main OS
/dev/hda3 is Share (FAT32)
/dev/hda4 is Ubuntu (a backup, in case Kubuntu gets screwed up.)
/dev/hda2 is an "extended partition"
--/dev/hda5 is a linux swap partition (inside the extended partition)

/dev/hdb is 40 MB contains only my Windows partition. /dev/hda is 80 MB.

What I'd like to do is: buy a 100 MB drive, copy the Windows partition to that, and use the remainder as a backup partition. My original plan was to buy a 250 GB external hard drive and have room for all my backups forever, but I'm saving up for a laptop instead. (I figure a smaller size, internal hard drive is much cheaper, and later I can make it into an external.)

Here's my problems:

Question 1: /dev/hda1 is definately my root Kubuntu partition, and it is marked with the "boot" flag in the Gnome Partition Editor (see screenshot); however it is the GRUB menu.lst in my *Ubuntu partition* (hda4) that is used! (I am positive of this, because I changed GRUB to use a 3 sec timeout and pretty colors.) Is the computer booting from hda4 then? How can I change it to boot from hda1? (I may be moving/deleting hda4, so I need to know.) Would I need to reinstall GRUB somehow?

Question 2: Given my configuration, what is the best way to copy my Windows partition to the new hard drive? I'm thinking of 1) pulling out my Linux hard drive and sticking in the new drive, so that the Windows hard drive and the new hard drive are the only ones connected, 2) using a live CD to copy the NTFS partition, and then 3) taking the Windows drive out and putting the Linux one back in. (I can only have two drives connected to the computer at once.)  Would it be better to use something like Norton Ghost instead?

Question 3: Will I be able to boot Windows by simply copying the NTFS partition to the first partition of the new hard drive? Because it would still be called /dev/hdb1, right?

Er... (looking at "GParted | Filesystems"), and Question 4: Can the Gnome Partition Editor even copy NTFS partitions? Is there a live CD that includes that ability?

Responses to any (or all) of these worries would be appreciated.

---

### Post by dcstar on 2007-01-26
> **kwilliam said:**
> 
.......
Question 1: /dev/hda1 is definately my root Kubuntu partition, and it is marked with the "boot" flag in the Gnome Partition Editor (see screenshot); however it is the GRUB menu.lst in my *Ubuntu partition* (hda4) that is used! (I am positive of this, because I changed GRUB to use a 3 sec timeout and pretty colors.) Is the computer booting from hda4 then? How can I change it to boot from hda1? (I may be moving/deleting hda4, so I need to know.) Would I need to reinstall GRUB somehow?

Question 2: Given my configuration, what is the best way to copy my Windows partition to the new hard drive? I'm thinking of 1) pulling out my Linux hard drive and sticking in the new drive, so that the Windows hard drive and the new hard drive are the only ones connected, 2) using a live CD to copy the NTFS partition, and then 3) taking the Windows drive out and putting the Linux one back in. (I can only have two drives connected to the computer at once.)  Would it be better to use something like Norton Ghost instead?

Question 3: Will I be able to boot Windows by simply copying the NTFS partition to the first partition of the new hard drive? Because it would still be called /dev/hdb1, right?

Er... (looking at "GParted | Filesystems"), and Question 4: Can the Gnome Partition Editor even copy NTFS partitions? Is there a live CD that includes that ability?

Responses to any (or all) of these worries would be appreciated.

1: There is a boot device which holds the Grub loader, then Grub is loaded and boots the O/S as per whatever you have set up in it (it don't really matter where the initial boot loader stuff resides).

2: The **partimage** utility is probably what you want, install it and have a play.

3: Maybe, maybe not......

4: Copying partitions like that may work, another thing to try (but be careful!).

---

### Post by highneko on 2007-01-26
Yea, partimage is nice. I suggest getting [http://www.sysresccd.org/](http://www.sysresccd.org/)

When the cd boots it doesn't mount anything so that you can save any partitions. There are some good tutorials with screenshots.

Boot systemrescuecd, then use "df -h" to find what device it's on or whatever.
Mount the partition where you wanna save the copied partition.
Then type "partimage".

---

