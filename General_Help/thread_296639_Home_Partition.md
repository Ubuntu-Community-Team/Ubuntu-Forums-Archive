---
title: "Home Partition"
date: 2006-11-09
forum: General Help
---

### Post by link141 on 2006-11-09
(I am exhausted, please pardon any details that have escaped my attention)

Hello Fellow Ubuntu users.  I have an installed copy of kubuntu Dapper on my computer, and am considering (leaning on) switching to edgy ((K/Ubuntu (and/or), perhaps)).  I do a lot of re-installs (I want a lean/mean system up!:)), and it would be useful if I could setup a 'home partition' on each re-install.  Currently, I've got an 80GB (really only 76-78 GB of usable space) drive that is partitioned into the following:  65GB FAT32 (windows linux share drive), 5.4GB (root), 5.4GB (Lin. Swap), and some 2.4GB NTFS (not certain how much space for windows).  I also have an ancient, noisy 10GB ATA drive--partitioned 10GB FAT32--, but lets not concentrate on that for the moment... 

I want to use the 68GB space as the home directory, and am not sure if Ubuntu will operate correctly with a FAT32 drive as the home directory.  My rationale (if that's how you spell it) behind this partition format choice, was that it could be accessed by MS Windows, but windows messes it up at the root of the drive (and every other level) with a folder called SYSTEM-INFORMATION, but I have a feeling this will mess up Ubuntu when trying to read it as a home partition.  I also have a feeling it may will run faster/cleaner with a native linux partition format (Ext2 or 3, perhaps...), are there any disadvantages to having it FAT32?

Anyway, I'm probably going to keep the old drive in the comp. for backup (and too use between this install), but leave it as an Ubuntu/Windows share space --windows contaminates everything!, and I found it very intrusive, and sporatic when functioning with another comp OS on the same computer-- and possibly get rid of windows altogether. 

Disregarding windows (or starting from completely clean slate), what is the best way to setup a simple, quick and stable home directory? My main (and highest priority goal) is to keep this system at it's simplest/fastest and secure against internet threats.  

If you decide to help me out, feel free to ask for any details that I missed or that will help with my intentions.  Don't knock yourself out, all I really need is advice on what the best home partition setup is, or for somebody to tell me an easy way to get a simple linux home partition up.    

I'm currently learning Ubuntu, and want to help in any way possible.  If I use Edgy, I'm probably going too do some bug testing...
 
Thanks guys,
Ubuntu enthusiast, link141

---

### Post by Sef on 2006-11-09
Windows is able to read and write to ext 2 and ext 3, so just format your home partition as that.

---

### Post by hearnden on 2006-11-09
I agree.  Just install this: [http://www.fs-driver.org](http://www.fs-driver.org), and you can access Linux ext2/3 partitions from Windows.

A FAT filesystem for your home partition shouldn't be a problem, but ext3 sounds better and safer (journalling has to be good for something).

Just curious, but 5.4GB for swap sounds awfully big.  The rule of thumb is 2xRAM, but it's debatable if swap above 2GB makes a difference.

Only 2.4GB for Windows sounds awfully tight too!  I'd recommend reclaiming 3GB of your swap partition for WIndows.  It's also perfectly possible to have Windows use a non-first partition.  I've currently got XP on my 4th primary partition.

I'm not sure if there's much you can do other than choice of FS and partition placement for a simple quick and stable home directory.  If you put your home partition closer to the start of the disk (i.e. the outer edges) it can be accessed faster, however I'd recommend putting your OS and swap there over home data.

---

### Post by aysiu on 2006-11-09
> **hearnden said:**
> 
A FAT filesystem for your home partition shouldn't be a problem It shouldn't?

---

### Post by hearnden on 2006-11-09
> **aysiu said:**
> It shouldn't?
should it?

(other than the general problems of FAT over ext3)?

---

### Post by iball on 2006-11-10
> **hearnden said:**
> should it?

(other than the general problems of FAT over ext3)?

Yes.
FAT does not support permissions and ownership, etc, like most decent file systems like ext3.  All your user files will have permissions 777 (rwxrwxrwx).

Also FAT is not a Journaled file system, so you will lose data if you get a sudden power outage.

--Ian

---

