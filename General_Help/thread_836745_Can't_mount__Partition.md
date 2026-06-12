---
title: "Can't mount  Partition"
date: 2008-06-21
forum: General Help
---

### Post by Blind Tiger on 2008-06-21
After a failed XP guest os virtual machine install using Virtual Box, my sda1 partition won't mount.  This was a data partition, and I had created a directory there to use as my virtual machine space.

How can I remount this partition to salvage all the other data I had on there???!!!

---

### Post by tamoneya on 2008-06-21
have you tried the force option.  NTFS partitions and I think FAT32 partitions get locked if they arent unmounted properly.  If you didnt properly shutdown and unmount in windows it would cause the partition to be locked.  Just add "-o force" into your mount command.

---

### Post by Blind Tiger on 2008-06-21
It is a reiserfs partition that I manually mounted after I installed Ubuntu many months ago.  

I tried booting in recovery mode, and noticed that there are multiple errors when trying to mount the local filesystem.  Superblock error for sda1, errno 16.  Am I screwed, or is there a way to at least salvage the data?

---

### Post by avtolle on 2008-06-21
If you have a Live CD for Ubuntu, boot into it; at the desktop, when you get there, Alt+F2 gets you to a window; in the blank, type in gksudo gparted, then run (hit OK, whatever, this is from memory). When it opens up, click on the partition where your data is stored and have it mounted. Exit Gparted. Back at the desktop, there may be an icon on the desktop representing the partition, with something about a volume and its name. Back to Alt+F2, this time gksudo nautilus to give you root authority. With any luck, you will be able to browse the files on that partition, and using Nautilus identify them for copying to an external device.

If you don't have a 8.04 or 7.10 Live CD, you could go to the Gparted website, and d/l an iso and burn it to CD so you would have a live cd of the partitioner. Again, you would mount the subject partition, but I believe (not having used a Gparted Live CD) you would need to do the copying to the external device vial the terminal. 

Good luck, and hope something in the above is helpful to you.

---

### Post by smo0th on 2008-06-21
good, let's suppose you have your partition mounted on /dev/hda1.

Run ```
reiserfsck --check --logfile check.log /dev/hda1
```

If reiserfsck --check exits with status 0 it means no errors were discovered.

If reiserfsck --check exits with status 1 (and reports about fixable corruptions) it means that you should run ```
reiserfsck --fix-fixable --logfile fixable.log /dev/hda1
```

If reiserfsck --check exits with status 2 (and reports about fatal corruptions) it means that you need to run reiserfsck --rebuild-tree.

If reiserfsck --check fails in some way you should also run reiserfsck --rebuild-tree

Before running reiserfsck --rebuild-tree, make a backup of the whole partition before proceeding. Then run ```
reiserfsck --rebuild-tree --logfile rebuild.log /dev/hda1
```

---

### Post by Blind Tiger on 2008-06-21
I tried the first check, but the partition in question, sda1, apparently did not get mounted.  While browsing with nautilus, the directory to which I mounted it is just empty.  If I do fdisk -l, the partition is not listed.  Is there a way to remount it to run the reiserfs check or fixes?

---

### Post by smo0th on 2008-06-21
let's try with ```
df
``` please paste this and the following command's output ```
sudo fdisk -l
``` it's important to use sudo when you do fdisk -l

---

### Post by Blind Tiger on 2008-06-21
> ~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdb2              5245016   4410428    834588  85% /
varrun                 1558176       248   1557928   1% /var/run
varlock                1558176         0   1558176   0% /var/lock
udev                   1558176       116   1558060   1% /dev
devshm                 1558176        16   1558160   1% /dev/shm
lrm                    1558176     34696   1523480   3% /lib/modules/2.6.22-15-generic/volatile
/dev/hdb4              2939744   1786592   1153152  61% /home
/dev/hda1             78140128  38530512  39609616  50% /media/hda1
/dev/hdb1             67657712  50150764  17506948  75% /media/hdb1

results from fdisk -l:

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfefdfefd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c4aab

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        8423    67657716    7  HPFS/NTFS
/dev/hdb2            8424        9076     5245222+  83  Linux
/dev/hdb3            9443        9729     2305327+   5  Extended
/dev/hdb4   *        9077        9442     2939895   83  Linux
/dev/hdb5            9443        9729     2305296   82  Linux swap / Solaris

Partition table entries are not in disk order

as you can see, sda1 is not being mounted at all, so the reiserfs commands will have no effect because /dev/sda1 is not found.

i think i completely fragged sda1 after my botched xp guest os install using virtualbox.

---

### Post by avtolle on 2008-06-22
Now I'm confused (easily done). The output of both commands makes me think there are two HDDs on your system, which are being identified as hda and hdb. Is there a third one?

---

### Post by Blind Tiger on 2008-06-22
yes, i should have clarified that.  i have windows xp installed on hda1.  hdb1 is my  ntfs data drive for xp.  hdb2-5 are partitions associated with my Gutsy install.  the third drive, sda, has two ntfs partitions used as backups for the two primary ntfs partitions, and a partition that I mounted to /mnt/newhome directory that i created.  it  is this last partition that will no longer mount when i boot.  i can watch it report errors from the command line as it tries to mount the file system.

also, the two ntfs partitions on the sata drive are not mounted ever -- i chose not to as they were backup partitions not needed for my gutsy os.

---

### Post by avtolle on 2008-06-22
Thanks for the clarification. Still haven't figured out anything to suggest other than what I did earlier, and thus I will leave you in smo0th's good hands.

---

### Post by Blind Tiger on 2008-06-22
see the output below:  sda1 is the partition that i seem to have fubar'd.

cat /proc/partitions
major minor  #blocks  name

   8     0  488386584 sda
   8     1   72510984 sda1
   8     2          1 sda2
   8     5   41943352 sda5
   8     6   83886232 sda6
   8     7    3145936 sda7
   3     0   78150744 hda
   3     1   78140128 hda1
   3    64   78150744 hdb
   3    65   67657716 hdb1
   3    66    5245222 hdb2
   3    67          1 hdb3
   3    68    2939895 hdb4
   3    69    2305296 hdb5

---

### Post by Blind Tiger on 2008-06-22
also, i tried the reiserfsck commands again, and get the following:
> 
bread: Cannot read the block (2): (Input/output error)

---

### Post by Blind Tiger on 2008-06-22
This is dragging on, I know, but as one last note, if I boot off of 8.04 live cd, sda1 is mounted, and I can browse the entire directory contained on the partition, but it appears that some data is corrupt.

I'm hoping to find a way to remount it when I boot off hardisk into Gutsy and salvage my data.

---

### Post by Blind Tiger on 2008-06-23
Yet another post -- Since sda1 mounted with the Hardy live cd, I was able to use reiserfsck, but regardless of the command I try, the result is  this:
> bread: Cannot read the block (2): (Input/output error).

I think this partition is toast, and I will have to either delete it or just leave it as dead and use the rest of the unallocated space for data use or another ubuntu install.

---

### Post by Blind Tiger on 2008-06-23
Tried all methods from manual to guided partitioning in an attempt to install Hardy to the disk with the corrupt  partition.  No luck whatsoever.  Looks like it is a dead drive, and reiserfsck advice was right -- not worth the time to try to fix it.  Time to get a new one!

I'll give it one last try using Acronis from XP to see if I can reformat the drive, but I doubt that will work as I already tried to create a new partition using the previously available free space and received an error.

---

### Post by Blind Tiger on 2008-06-28
No success with Acronis Disk Director.  Used WD diagnostic/repair utility, returned unrepairable state.  So the disk is now off to warranty.

---

### Post by smo0th on 2008-06-30
omg sorry to leave you alone all this time, shame that your hdd turned out to be damaged, good thing you had a warranty to claim, see you around ;)

---

### Post by Blind Tiger on 2008-06-30
No worries.  I did all feasible diagnostics and repair efforts with no success.  So a few days from now I'll have a spankin' new drive.

---

