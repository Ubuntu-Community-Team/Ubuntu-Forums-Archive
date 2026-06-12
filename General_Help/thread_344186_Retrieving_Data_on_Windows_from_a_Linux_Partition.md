---
title: "Retrieving Data on Windows from a Linux Partition"
date: 2007-01-22
forum: General Help
---

### Post by Goober on 2007-01-22
Wow, it has been ages since I was last here ... 

Ok, here is my situation - I had 2 hard drives, a 40 gig that was my main hard drive (primary), and had Windoze installed as well as GRUB to access my Hoary Partition.  On my secondary Hard drive, I had it partitioned into space for Windows storage, and I had Hoary installed.

Then my 40 gig, which was 4 years old, decided to stop functioning, as in, it is now an overpriced paperweight (literally).  This wasn't terrible since I had been expecting this, and everything was backed up on my secondary drive.  So I made the secondary drive my primary, and installed XP on that.  But I couldn't (and still can't) access my Hoary files, since GRUB died along with my primary hard drive.

What I want to do is retrieve some of the files I had on my Hoary partition onto the XP partition, then format the Hoary partition, and install the latest version of Ubuntu, time permitting.  So, in a sense, I want to move files from the Hoary file system, ext3 or something like that, to NTFS.  Can I do this?  If so, how?

I would really appreciate any help.  Thanks in advance!

---

### Post by Hossie on 2007-01-22
I think there's an ext3 driver, but I think the much better solution is to use a LiveCD like Knoppix (or maybe your Ubuntu Installer CD), modern LiveCDs support writing to NTFS.

---

### Post by Goober on 2007-01-22
So you mean get a live CD, and then mount my Windows partition, and click and drag the files onto the partition?  Should I get the 6.10 Live CD, or will the 5.10 one work?

---

### Post by Hossie on 2007-01-22
I'm not sure if the Ubuntu CDs have NTFS write support. It's much safer to get a recent "real" LiveCD like Knoppix.

&#8364;: If you have some free space left, it maybe a good idea to create a new partition with FAT32 and put your files there, its always a risk writing to NTFS.

---

### Post by david_2001 on 2007-01-22
As an alternative, in the days when I dual-booted I used to use Explore2fs ([http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)) to access my ext3 Linux partitions from Windows.  There is also the DiskInternals Linux Reader ([http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)) but I didn't find it to be quite so flexible.

---

### Post by Goober on 2007-01-22
Thank you very much David, I was hoping a program like those existed.  I seem to have run into a new problem.  Using the second program you listed, the Linux Reader, I have determined that the partition isn't being read as ext3, which I am sure it is, but "FAT 16 lba".  I know the program works because it reads my Windows partition as NTFS, which it is.  FAT 16 is an ancient Windows filesystem.

I guess I'll need to dig up my 5.10 LiveCD and see what is wrong ...

---

### Post by Goober on 2007-01-22
Well, I dug up my 4.10 LiveCD (Not sure where the 5.10 went to), but I think that partition is fried somehow.  I am presently using the 4.10 LiveCD (Ahh, the good 'ol Days of Warty), and it shows 3 partitions, hda2, 3, and 5 (Not sure why not 1, 2 and 3, but oh well).  hda2 and 3 are my Windows ones, and hda 5 must be the Linux one.  I can mount hda 2 and 3 just fine, but I cannot mount hda 5, which indicates that it is likely not functioning. I guess it got corrupted somehow.  I am going to get back my 5.10 liveCD, and double check, but it seems that my Linux partition is fried.  And I doubt there is a program that will let me get them back, as there are for some corrupted Windows partitions ... 

Ah well, thanks for the help guys!  I really appreciate it!

---

### Post by david_2001 on 2007-01-22
Sorry to hear that :(.  I've never had to recover data from a corrupted hdd, so cannot be a lot of help.  However, the device numbers you're quoting definitely don't seem to be quite right.  There ought to be an sda1, though sda4 could possibly be an extended partition.  Anyway, Google might be your helping hand with this dilemma - a quick look suggests that you can either pay money for recovery software or try using fsck ([http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)).

---

### Post by drpaul on 2007-01-22
sda... is for SATA drives. hda... is for IDE drives. 

Or so I think.

Paul

---

### Post by Sef on 2007-01-22
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") to possibly recover your partitions.

Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12") to possibly recover your data.

---

### Post by Goober on 2007-01-22
David, just so you know, there was something labelled sda with a number, i think it was 5.  I ignored it, because hda5 is where the partition should be.

Thank you Sef and David, I will try those next.  I'm honestly not sure why it is corrupted, I know it was working a couple months ago when I last accessed it ...

One thing I don't understand is that is it a totally different file system, FAT 16.  Is it possible for ext3 to become FAT 16?!?!

---

### Post by Sef on 2007-01-22
> One thing I don't understand is that is it a totally different file system, FAT 16. Is it possible for ext3 to become FAT 16?!?!

No, unless it was reformatted.

---

### Post by david_2001 on 2007-01-23
> **drpaul said:**
> sda... is for SATA drives. hda... is for IDE drives. 

Or so I think.

Paul

Unfortunate slip of the finger (I've got 2 x SATA drives).

---

