---
title: "Migrated RAID card and HDDs to new machine... Boot issues..."
date: 2012-10-23
forum: General Help
---

### Post by DeadlyOats on 2012-10-23
The motherboard on my old machine died.  I built a new machine.  I figured I'd move the RAID card, an Adaptec 2410 SA and my two Raptor SATA drives set up in RAID - on THAT card, and move them to the new machine.

The Adaptec RAID card started up fine.  Grub started up fine.  However, when I tried to start Ubuntu 11.10, it failed to start.  I get some text, and it says something like it can't find root (or did it say "/ (root)", and asks me to fix the partition, or words to that effect.  (I wonder if the problem might be because the swap was set up on a physically separate HDD?  I didn't move the other HDD over to my new machine.  That other HDD is a PATA HDD and not a SATA HDD, and my new machine does not have any legacy IDE connections for the old PATA HDD.)

I'm using the Kubuntu Live CD to type this.  I used "Partition Manager"; it found my / and /home partitions.  I right clicked on each of them, and clicked on the "check" menu item for both.  It said it successfully checked and repaired the /, and later the /home partition, but then on reboot, I got the same problem.

Any ideas on how to fix? 

Thanks.

---

### Post by awr on 2012-10-23
By the sound of your post, the two PCs are different.  Which means hardware addresses and how Linux sees your hardware will also be different.  Unless the two PCs are identical hardware this type of move will usually result in more trouble than it is worth.

My suggestion, backup your data, move the card and drives, then do a fresh install of Linux/Ubuntu on the new machine.  Then restore your data on the new build.

---

### Post by DeadlyOats on 2012-10-23
Hmmm.....  They are not the same hardware.  Tsk!  :frown:

O.K., then.  How about this. [-o<   Is there away for me to access my files in my install, then copy paste them to an external drive?  If I can do that, at least, then all is not lost.  [-o<  Moving the RAID array back is not an option.  The mobo is dead in the old machine.

Thanks.

---

### Post by awr on 2012-10-23
You could potentially boot from a Live CD then mount the volumes from there to copy your data over to another HDD or a USB disk or similar, assuming the Live CD can read your disks.

---

### Post by DeadlyOats on 2012-10-23
It's already mounted, but the home folder is blank.  Can't see the contents of the home folder...

So, how do I access the files so that I can copy/paste them to my external HDD?

---

### Post by awr on 2012-10-23
Can you mount the root filesystem, and can you see files there?  If you can and presuming you didn't have an encrypted /home, then I'm out of ideas.  I suspect your files are gone.

---

### Post by DeadlyOats on 2012-10-23
Yeah, the hard drive files are showing in dolphin, but /home is empty.  I think it's that way to protect the files there, but I know the user name and password, is there a way to access my stuff from the live CD, or is there not?

---

### Post by awr on 2012-10-23
Not trolling.

If you can mount the / (root) filesystem on your raid and read the files, then it would be logical that you should be able to do the same in /home (meaning your disks are probably fine and readable).  If you can't read the root filesystem then there is likely a problem with the raid setup in the new machine and until that is fixed (if it can be) you won't be able to recover your files from /home either.

Make sense?

---

### Post by DeadlyOats on 2012-10-23
I click on the icon representing the hard drive, and I see all of the folders in there: bin, boot, dev, etc, home, .....  I can see the items in all of those folders, but when I click on the /root folder, and the /home folder, those are empty.

I think they're hidden.

EDIT: I see my username ( /home/username ) folder too, but it's empty.

---

### Post by awr on 2012-10-23
> **DeadlyOats said:**
> I click on the icon representing the hard drive, and I see all of the folders in there: bin, boot, dev, etc, home, .....  I can see the items in all of those folders, but when I click on the /root folder, and the /home folder, those are empty.

I think they're hidden.

EDIT: I see my username ( /home/username ) folder too, but it's empty.

Can you get yourself around from a command line (terminal) or do you rely on the GUI?

If you know how to use a terminal, what is the output of 

```
sudo fdisk -l
```

---

### Post by DeadlyOats on 2012-10-23
Here's what I got.

```
kubuntu@kubuntu:~$ sudo fdisk -l

Disk /dev/sda: 148.6 GB, 148597768192 bytes 255 heads, 63 sectors/track, 18065 cylinders,
total 290230016 sectors Units = sectors of 1 * 512 = 512 bytes Sector size
(logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 
bytes Disk identifier: 0xca71ca71

 Device Boot    	    Start         End      Blocks   Id  System
	/dev/sda1   *        2048    29300735    14649344   83  Linux
	/dev/sda2        29300736   290228223   130463744   83  Linux 
kubuntu@kubuntu:~$

```

---

### Post by DeadlyOats on 2012-10-24
:oops: Shamefully :redface: , shameless bump.  :tongue:

---

### Post by awr on 2012-10-24
Keep bumping, and I'll ignore this post.  And perhaps you could do a little research on your own with the hints we have been giving you, maybe you'll work it out on your own.

Post the output of the following commands also (AFTER you have mounted both / (root) and /home):

```
sudo lsblk
```

---

