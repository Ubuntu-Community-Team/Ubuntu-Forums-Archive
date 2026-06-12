---
title: "Random HDD screw up"
date: 2014-03-19
forum: General Help
---

### Post by Tristan_Williams on 2014-03-19
I had Ubuntu Minimal 13.10 installed on a Toshiba HDD.
I just had to install Xubuntu on my spare HDD because the Ubuntu Minimal drive is unbootable, unreadable, and completely ****ed.

Trying to mount it from Xubuntu results in countless errors.

I had a lot of important home-school documents on there.

It will boot and give me a grub-rescue prompt, but absolutely nothing works.
Again, I can't mount it from Xubuntu, and I can't mount it from any Live-CDs.

What could have caused this?
I haven't been playing with partitions or anything like that. I try to keep good care of this system because of the home-school.

---

### Post by efflandt on 2014-03-20
You never know if a hard drive will last forever, or suddenly fail. For example several times over the years I have had drives fail under warranty, and the warranty replacement drives still working after more than 10 years. So it is best to keep a backup of anything your really do not want to lose in another place.

Drives reserve space to automatically and transparently remap reserved good sectors in place of bad sectors, so if you start actually noticing bad sectors, that is a sign to back up or preserve anything you can on the drive that you have not already backed up. The drive on my desktop from 2004 has never had any problems and is still running fine. But the far end of the drive on my 2010 desktop where my Linux partition was began failing after about 3 years. One sign that it was going bad is that there were times when I could not write files to the drive because it had automatically remounted read only due to errors. I could only nurse it along with e2fsck (along with parameters to lock out badblocks) so many times before it got worse. Fortunately I was able to image the Windows partitions and put them on a new drive, reinstall Ubuntu on the new drive, and copy my /home directory over. Only a few game files were corrupted which Steam was able to replace.

But if your drive had something like electrical failure or a head let go, it might just be a loose cable, or it may be beyond hope (very expensive and uncertain to recover data). Does **sudo fdisk -l /dev/sdX** (where X is whichever drive letter) still show drive and partition info? If that cannot even detect the drive, you have a real problem. If that does detect the drive you may be able to **sudo e2fsck -p** (or possibly other parameters) Linux partitions if ext2, ext3, or ext4 to try to temporarily restore them. Or if partitions are messed up you could try **testdisk** to see if it can recover any files.

In one case I was trying to help someone recover a Windows drive on an old laptop which refused to boot. I booted Ubuntu live/install CD and started copying files from it to external drive when it suddenly choked. I put the drive in a USB enclosure and neither Windows nor Linux could mount anything on it. But a week or two later I plugged it into my Ubuntu desktop, it automounted, and I was able to copy most of the user's files from it except for a corrupted game directory.

It would help if we knew what errors you were getting about the drive, either in your logs or when you try to mount partitions from it. Most logs are in /var/log or you can type **dmesg** (or **dmesg | less**) to see recent log info during since current boot.

---

### Post by Tristan_Williams on 2014-03-20
'fdisk -l /dev/sdb' puts this out:
```

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bac10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   616824831   308411392   83  Linux
/dev/sdb2       616824832   625141759     4158464   82  Linux swap / Solaris

```

I used testdisk to copy data from the homeschool user profile onto a mid-point folder, then copied the files I needed to the new profile. 
It showed 37,000 files were ok and were copied... But then looking at errors... 2,500,000
There were a lot of things out of place and some files I've never seen (like in the music folder. Should have been empty)

On a related note, I noticed that testdisk could read deleted files. Which both gives me an evil grin, and kind of scares me...

Overall, I think testdisk was the best thing I could have come across for this particular problem. Thanks everyone :)

---

