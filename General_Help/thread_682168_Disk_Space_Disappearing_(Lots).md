---
title: "Disk Space Disappearing (Lots)"
date: 2008-01-29
forum: General Help
---

### Post by Zebediah49 on 2008-01-29
I have scanned over the threads that I could find on here and other places, and though I found a number of similar problems, none of the solutions seem to work for me.

My problem is best summed up by this image: 
[IMG]http://img521.imageshack.us/img521/3344/discspacemissingft0.png[/IMG]

As you can see, the sum of all my files is almost 100 GB below what it thinks they're using, and I can't figure out why.  I have deleted the contents of /home/me/.Trash, /media/disc/.Trash-me (that's where it's mounted), and have looked for hidden folders, all to no avail.

It is beginning to concern me, since eating 20% of my total space is kind of bad.

If anyone has any ideas, I would appreciate some sort of resolution to this.

--------
Other Info/ stuff I've tried.
1. If it matters, a couple of times the drive has not mounted properly (actually, it wouldn't recognize it).  Turning it off and then back on a few seconds later solved the problem.
2. If I try to use a partition tool on it, it refuses to touch it, saying that I need to run chkdsk in windows.  I'd rather not, since windows takes about half an hour to boot, when it does (it's my own fault, but still; I also don't actually need to since I can just use ubuntu here and it's fine).
3. Might it be something do do with NTFS, and it would be a better idea to use ext3 and to install a windows driver for that? (sounds like a questionable idea, but I've never tried it)
4. du -h --max-depth=1 returns just what I expect it to: the files and folders that I have there, totalling 355G.
5. df -a returns what I don't expect it to: "/dev/sdb1            488384000 471357448  17026552  97% /media/disk"

---

### Post by Shazaam on 2008-01-29
You need to run chkdsk on the ntfs partition.
If you have Gutsy installed you should already have read/write access to your ntfs partition. Can you tell what Windows folder is taking up the most space? I had a problem once with Roxio that filled up a hard drive in 5 minutes.
A few more questions-- Is this a VMware install? Or a WUBI install?

Please post the output of this terminal command....
```
sudo fdisk -lu
```
This code will print out your hard drive info. Copy and paste it here.

---

### Post by prince_niceguy on 2008-01-29
run the disk analyzer utility under accessory and it will give you exact details about which folder is taking space, might give your more details about it.

If it is trash only and it is on separate partition then try formatting it, or deleting and recreating the partition.

---

### Post by Zebediah49 on 2008-01-29
> **prince_niceguy said:**
> run the disk analyzer utility under accessory and it will give you exact details about which folder is taking space, might give your more details about it.

If it is trash only and it is on separate partition then try formatting it, or deleting and recreating the partition.

I know what of my own stuff is taking the space.. the problem is that it's either more invisible than hidden, or it's not really there.  the sum of all files is 355; I know about what causes that.

@Shazaam:
```

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000098ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    7  HPFS/NTFS

```

and no, it's independently installed as another partition on my internal hard drive.  Do you need the specs on the laptop and the install?  I would think that that's outside the scope of this, but if you want it...

---

### Post by Shazaam on 2008-01-29
No I don't need the specs.
Sorry, I was running Dapper at the time I originally replied. I am now running Gutsy and looking at the properties window for my Windows drive (at /media) and I see a similar problem with incorrect and conflicting information. I have an 80 gig drive with XP (ntfs) installed and the properties window has similar differences in size of drive and total file size. Mine has a .7gig difference that may be attributed to drive size and amount of files compared to yours. Looks like a glitch somewhere so if you are concerned you might file a launchpad bug report. I normally use Dapper and it reads correctly (has no pie chart in the properties window) for me.

---

### Post by Zebediah49 on 2008-01-29
> **Shazaam said:**
> No I don't need the specs.
Sorry, I was running Dapper at the time I originally replied. I am now running Gutsy and looking at the properties window for my Windows drive (at /media) and I see a similar problem with incorrect and conflicting information. I have an 80 gig drive with XP (ntfs) installed and the properties window has similar differences in size of drive and total file size. Mine has a .7gig difference that may be attributed to drive size and amount of files compared to yours. Looks like a glitch somewhere so if you are concerned you might file a launchpad bug report. I normally use Dapper and it reads correctly (has no pie chart in the properties window) for me.

Ah, I guess I'll go for it and see if windows can deal with it proplery.

What concerns me is that the space-left counter still works the same way, so if I use my 'remaining' 16 G, it'll probably deny me more space.

Thanks anyway though.

---

