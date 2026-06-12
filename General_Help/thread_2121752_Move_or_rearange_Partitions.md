---
title: "Move or rearange Partitions?"
date: 2013-03-02
forum: General Help
---

### Post by daldude on 2013-03-02
Is there a way to move a linux system partition without breaking the Linux install? I got a new hard drive and after cloning my old drive I have an extra 500gb of un used space and want to combine it with the space from my old drives data partition so I don't have 2 seprate partitions and don't want to have to reinstall Linux because it took me a while to get all my programs installed and settings the way I want them and I did the mod that makes 12.04 look more like 10.04 and did the MAC Lion Theme Mod and don't want go th all the time consuming steps to get it all set up again.

---

### Post by carl4926 on 2013-03-02
Is the space you want to combine on the same HD?
Open Gparted and take a screen of the partitions and add some explanation of what you want

---

### Post by von Corax on 2013-03-03
Agreed - gparted is the tool you want. You'll find it on the LiveDVD, and you'll need to boot the LiveDVD to use it, as the disk you're modifying must be unmounted at the time. Gparted's built-in documentation should explain the process clearly. (I just got done resizing partitions on a 1TB drive; it was reasonably simple but took a *long* time.)

Good luck.

---

### Post by chocklet on 2013-03-03
Assuming that
- the new drive is the boot drive, sda
- your original system was the boot drive, originally sda, but now has become sdb
- you've "cloned" the original system, which was boot drive, sda, to the new drive (boot drive, sda)

> **daldude said:**
> Is there a way to move a linux system partition without breaking the Linux install?

Yep.  You cloned it.  It should just work.  (assuming that "cloning" includes the boot loader and the BIOS selects the new drive)

If you update grub you will see that it will find your original install that is now on sdb.  If you select it at the updated grub menu, you may see that your original system still works (uncertain how well).

That's all pretty straight forward, so maybe my assumptions are off.

It appears that your other question is buried in that excellent sentence with no commas!  Is it something like this?...

"How can I combine the "old drives data partition" with the "extra 500gb of un used space" on the new drive, so I "don't have 2 seprate partitions"?

If that is your question, then it's over my head.  Certainly there are people here who can figure out how to do almost anything if they have a clear understanding of the question.

I'm stealing this line from gogalthorp in another forum...

"LVM does not merge partitions it does merge file systems on multiple partitions. But you have to create LVM partitions to use it. Does not work on any old partition. "

  Yep, way over my head and may involve lots of effort, but LVM is a way to create one file system that spans partitions on different hard drives.

[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

You've been around here for years but just in case you forgot... be certain that your data backup is current.

---

### Post by oldfred on 2013-03-04
If you cloned drive and have both drives still plugged in you will have issues. You cannot have duplicate UUIDs and a full clone copies UUIDS. I normally suggest a new install and copy /home. And prefer /home be in a new partition so system partition is small.

If you want to keep old drive plugged in, you will have to change UUIDs, edit fstab and grub with new UUIDs on one system or the other.

Post this using liveCD or flash drive:
 # To clear cache and get new view:
sudo blkid -c /dev/null -o list

---

### Post by daldude on 2013-03-04
What I want to do is merge 2 partitions into 1 partition so the 1 partition has the combined space of both partitions but the problem is the 2 partitions are seprated by my Linux System Partition and Swap Partition. I cloned a 500gb hard drive to a 1tb hard drive so half the drive is unused and I want to use that extra space and add it to my exsisting partition I use for data storage. If I could somehow move the Linux System partition and Swap partition to the end of the free space on the 1tb drive and then merge the remaining space with my exsisting that might work but I don't know how to do that but I don't know if that will break the Linux Install because grub loader will be looking for the Linux Partition in the orginal place where it no longer existsts plus all the programs might have the same problem and there for will not run.
There is a program called Partition magic but that costs money.
I think the only way to do what I want is to delete my Linux System and Swap partitions plus my old Data Partition (that I've backed up all the data on) and then creat a data partition using Windows 7 leaving 150 GB for Linux and then reinstall Linux.

---

### Post by carl4926 on 2013-03-04
> **carl4926 said:**
> Is the space you want to combine on the same HD?
Open Gparted and take a screen of the partitions and add some explanation of what you want


Like I said
A picture so we can see what you have....

---

### Post by daldude on 2013-03-05
I want to combine the NTFS DATA-MP3 and NTFS DATA-MP3b partitions to make one larger partition but as you can see my Linux System and Swap Partitions are in between them.

---

### Post by carl4926 on 2013-03-05
It's possible tricky and very time consuming
sda7 is in the extended space and sda3 is a primary

So you would need to shrink sda7 so as to be able to shrink the extended
But you need to free the space on the correct side, that is next to sda3

Whatever you do Backup

---

