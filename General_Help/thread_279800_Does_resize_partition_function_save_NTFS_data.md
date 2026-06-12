---
title: "Does resize partition function save NTFS data"
date: 2006-10-18
forum: General Help
---

### Post by HalF on 2006-10-18
I am Trying to install Ubuntu on an Windows XP NTFS desktop (Dell Dimension 8200).  I want to save the Windows environment because of the years of data I have accumulated.  I cannot find any guide or reference which explicitly says that the Ubuntu partition resize process will save the data. 

I first tried to install Ubuntu 6.06 from a DVD included in the back of "The Official Ubuntu Book".  Unfortunately the PC BIOS does not recognize the aftermarket DVD drive as a possible boot device.

I then tried to install Ubuntu 5.10 from a CD, up to the point where it gave options for partitioning.  There was a check box for resizing, but nothing which says the equivalent of "will save your data".

I have succesfully installed SUSE Linux on a laptop using YaST while saving the Windows environment.  So I know it can be done.

Questions:

1.  Will Ubuntu 6.06 partitioner resize Windows NTFS and save the data?

2.  Same for Ubuntu 5.10 partitioner.

3.  If neither of the above, then how can I do this without using a commercial product?

---

### Post by aysiu on 2006-10-18
It won't *save* the data, but it should *preserve* the data in 99% of cases (be sure to defragment beforehand).

If you don't want to take a chance on that 1%, back up your data first, though.

---

### Post by HalF on 2006-10-18
Thanks, aysiu.  I will back it up first.

---

### Post by nacholand on 2006-11-13
hi,
I was looking for info on this subject and found this.
my problem is I have a whole hard drive with XP pro in my laptop (it's a Packard Bell EasyNote with an Athlon XP-M).
PQ partition magic keeps on giving me the error 117 'cannot find drive letter' and I can neither even run an older DOS version of PM from a bootable cd.
would it trustful to resize and partition with the ubuntu partitioner? do you think it may have a better NTFS compatibility in this new version?
thanks in advance.

Jose

> **aysiu said:**
> It won't *save* the data, but it should *preserve* the data in 99% of cases (be sure to defragment beforehand).

If you don't want to take a chance on that 1%, back up your data first, though.

---

### Post by ReaderRat on 2006-11-13
FYI -
If you want a look at your partition info, and want to resize, without doing an install, you can download [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php) and burn it to disc. The disc is bootable.

---

### Post by aysiu on 2006-11-13
> **ReaderRat said:**
> FYI -
If you want a look at your partition info, and want to resize, without doing an install, you can download [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php) and burn it to disc. The disc is bootable.
I thought the Ubuntu Desktop CD already came with GParted--no need to download GParted separately.

---

### Post by CatKiller on 2006-11-13
> **aysiu said:**
> I thought the Ubuntu Desktop CD already came with GParted--no need to download GParted separately.

It does, but it's an older version. The GParted cd version can do some things - like moving the start of an ext3 partition - that the version on the Ubuntu cd can't. Since a lot of posters here want to move the start of an ext3 partition, it gets recommended a lot. And you don't have to turn off your swap.

---

### Post by jerrylamos on 2006-11-21
Hi, interesting dialog to me - I've an IBM ThinkPad 1.066GHZ Celeron 504MB with partitions as displayed by defragger:

3.3 G in some sort of recovery partition not usually visible
17.69 G in 1 partition, 62% free space, 10.98 GB free.  That would be enough space BUT:

The kicker is a big splat of green "unmovable files" way out in the partition with only 3G free space after it, measuring from the screen display (how's that for precision).  The rest of the 7.98 GB free is in three chunks in the middle plus a lot of little chunks.

Yes, I've defragged several times, however there is only 3G left at the top. 

Gparted either on its own CD or on Dapper 6.06.1 only display the totals.  If I resize down 3G, what's chances gparted will chop off live data?

BTW, persistent works O.K. except for very slow boot stalling for minutes at odd places.  Not very tolerable for a class demonstration making Ubuntu look bad.

Maybe running off USB would be better but Xubuntu Edgy install on a 2GB USB gets a grub install error which no one in launchpad has looked at.  So far no luck with super grub putting grub on the usb either.  After attempted grub install there are odd things like /grub is in / instead of /boot.  Supergrub won't boot the USB either unless I'm running it wrong.

Any ideas?  Thanks much, Jerry

---

### Post by CatKiller on 2006-11-22
> **jerrylamos said:**
> The kicker is a big splat of green "unmovable files" way out in the partition with only 3G free space after it, measuring from the screen display (how's that for precision).  The rest of the 7.98 GB free is in three chunks in the middle plus a lot of little chunks.

Yes, I've defragged several times, however there is only 3G left at the top.

Gparted either on its own CD or on Dapper 6.06.1 only display the totals. If I resize down 3G, what's chances gparted will chop off live data?

It won't be live data, because it won't be mounted, since you'll be running the live cd rather than Windows. The only reason Windows can't move those files is because they're being used to run Windows to move the files. GParted should be able to move them fine. The reason for defragmenting is partly to save time, and partly as a just-in-case kind of thing.

---

### Post by jerrylamos on 2006-11-25
Well after defragging with Windows (wimpy) and a commercial defragger 30 day free trial, most of windows wound up in the first 6GB, then a big hole of 8GB, then about 0.8G immovable data, then 3G of free space at the end.

With Gparted I resized as much as I dared, down nearly 3G.  Then Windows had the first 6GB, the same big hole of 8GB, and then the same immovable data smack up at the end of the partition.  I'm dead sure if I had resized more with Gparted it would have gleefully chopped off the immovable data permanently killing XP.  I'm not going to try since it would be a real mess to get XP going again.

So install of Ubuntu 6.06.1 LTS said it needed "2G plus 256M for swap".

With 2G that it asked for, install failed with "no space on device".

The best I could squeeze out was 2.7G for / and 256M for swap.

It installed O.K., dual boot worked (yesterday, that is), and there certainly isn't much space for updates.

Oops, Ubuntu just died "checking all filesystems".  It's complaining about /dev/hda2 which is a hidden partition with IBM laptop installed support.
Ubuntu has no business messing around with that, file checking it, reading it, or anything else.  And no, it never did have Linux superblocks nor should it have, and it is certainly not ext2.  fstab thinks it is vfat.

Whew.  XP came up when selected from Grub.

Ubuntu boot up died again, same complaint about trying to "check all filesystems" and accessing a partition that does not belong to Ubuntu.
"enter", "exit" and Ubuntu came up.

Ubuntu is going to look great on the big screen when I show it to my class and boot up fails with "checking all filesystems", every time.

How do I tell Ubuntu to keep its hands off partitions that don't belong to it?  Thanks much, appreciate any hints.  

*** Answered my own question.  # commented out /dev/hda2 in /etc/fstab.
Boots up clean now, who knows about tomorrow.

Jerry Amos

---

### Post by CatKiller on 2006-11-25
> **jerrylamos said:**
> I'm dead sure if I had resized more with Gparted it would have gleefully chopped off the immovable data permanently killing XP.

I'm sure you know best.

It pays to be careful anyway. You have made backups, right?

Good luck.

---

### Post by louieb on 2006-11-25
> Ubuntu is going to look great on the big screen when I show it to my class and boot up fails with "checking all filesystems", every time.
Remove the partition from /etc/fstab or change the entry to the correct file system type. 
I get that file system check message when I change the file system on a partition. 
Looks like the installer did not get it right the first time.
Ubuntu not trying to mess with the partition but is trying to mount it so you can mess with it.

---

### Post by moshuptrail on 2006-11-25
Jerry -
You might have missed one of the previous posters...
Your XP partition was 6G (XP) + 8G (empty) + 3G (immovable) = 17G
You can safely resize this down to 10G and Gparted will move the immovable files.  They are only immovable to XP.
That will give you 7G for Ubuntu.  You'll need 4G for / and .5G for swap, and the remainder can be /home

---

