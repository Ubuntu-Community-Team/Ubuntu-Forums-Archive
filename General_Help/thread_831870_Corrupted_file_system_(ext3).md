---
title: "Corrupted file system (ext3)"
date: 2008-06-17
forum: General Help
---

### Post by mivo on 2008-06-17
About a week ago a storm caused a brief power outage, which apparently messed up my machine's ext3 file system. After the outage, it booted fine (it ran a file system check), but after today's kernel update and a reboot, fsck reports a problem and then apparently hangs at fixing it.

/dev/sda1 is fine ("clean"), but /dev/sda2 (which is /home) "contains a file system with errors" and a "check is forced". At about 70%, a message appears: "Duplicate or bad block in use!", and then it just sits there.

What should I do? I can skip the check and boot into Ubuntu just fine, but how do I properly correct this error before it gets worse?

---

### Post by prshah on 2008-06-17
> **mivo said:**
> 
 /dev/sda2 (which is /home) "contains a file system with errors" 
At about 70%, a message appears: "Duplicate or bad block in use!"


Looks like you have a bad block, which could well be caused by the power outage. Boot with a live CD. Ensure that all partitions on your hdd are UNMOUNTED, and swap is turned off. (sudo swapoff -a) Use the command```
sudo e2fsck -c -v /dev/sda
``` to check for badblocks, and mark them so that they will not be used again. If you have the time, you can run a much more through (but much longer) check with ```

sudo e2fsck -v -cc /dev/sda
```

Replace /dev/sda with your actual hard disk device. If there are too many bad sectors (blocks), maybe you should think about replacing the hard disk.

I'd suggest a backup of your important files before you do anything.

---

### Post by mivo on 2008-06-17
After posting my message on a different computer, I came back to the one with the corrupted file system and found that there had been a message after at least 30 minutes of no activity. It reported a "multiply-claimed block shared with 1 file" (long inode # and mod date follow) and then "fsck died with exit 4". It dumped me in a service shell and I typed "fsck" which started e2fsck. It is now "checking inodes, blocks and sizes" without any progress indication, but there is drive activity.

Edit: I saw there was a response while I typed. Thanks! I'll try this if just running fsck doesn't yield results (I don't know if I should interrupt this now). If my error only affects 1 file (from May 8), I'm a little relieved.

---

### Post by mivo on 2008-06-17
Another update: The plain fsck command seems to have produced results. It was "reconciling multiply-claimed blocks" and asked a number of questions with the default of "yes", i.e. if I want to clone the multiply-claimed blocks, clear the HTREE index, fix the "ref count" (2 instead of 1) of about 25 or so items, correct the "free block count" and attach unattached inodes to lost+found. I confirmed all of those with "yes". It seems to have worked. There are some files in lost+found now, all of which seem fine too -- just some text files that I also had backups of).

Is my file system fixed now or are there any other steps I should take, or any checks that I should perform (i.e. those explained in prshah's post), just to be on the safe side? I'd ideally like to avoid any long-term effects, i.e. noticing in a few months that some work-related files and their backups are trashed. ;)

---

### Post by Habbit on 2008-06-17
> **mivo said:**
> Is my file system fixed now or are there any other steps I should take, or any checks that I should perform (i.e. those explained in prshah's post), just to be on the safe side? I'd ideally like to avoid any long-term effects, i.e. noticing in a few months that some work-related files and their backups are trashed. ;)

To be on the safe side, I'd boot into "recovery mode" or "single user mode" (in the GRUB menu) and run "fsck.ext3 -f" on all your partitions - that will perform a pretty complete check except for bad blocks. If you have a lot of time (~ 4 hours at least) and want to be on the really safe side, run a "full HD surface" check for bad blocks, either with prshah's method or with HD manufacturer tools like Seagate's Seatools, which I find particularly useful.

Remember that the journaled filesystems of today protect you against FS inconsistencies caused by a crash/sudden loss of power - though, as you witnessed, these protections fail sometimes - and allow post-crash fsck's to be orders of magnitude faster, but there is _no_ protection whatsoever against physical HD failures. Nevertheless, all modern HDs have lots of spare sectors which are invisible to the system until a visible sector fails - then, bad sectors are remapped to the spare sectors and life continues to be nice. If your HD has bad sectors _and_ Seatools cannot "repair" them (i.e. remap them, either with or without loss of their data), then your HD has depleted its store of spare sectors and you would better start thinking of replacing it, since from that moment on everything goes downhill.

---

### Post by prshah on 2008-06-17
> **mivo said:**
> 

The plain fsck command seems to have produced results.

It was "reconciling multiply-claimed blocks" 

Is my file system fixed now or are there any other steps I should take


Considering that the error message said "bad blocks _or_ duplicate blocks", and that the final result found and corrected a duplicate block, I'd say you don't need to do anything more.

Running a bad block test about once in six months is a good practice (more often for laptops), but it takes soooo long to run that I keep putting it off. 

I'd suggest you budget a night run some day in the future to run a badblock check, right now doesn't seem necessary. 

And do consider a UPS if you lose power often; this, more than anything else, is the main culprit for bad blocks; closely followed by jars and jerks when the HDD is active.

On a side (informative) note; running plain fsck simply launches the correct fsck for your filetype; in this case, fsck would have simply passed the ball to e2fsck. Both are the same, and either are OK, but I prefer to use e2fsck in case any of the switches I use are e2fsck specific. (Or maybe because I'm just too damned particular).

---

### Post by greco8523 on 2008-06-18
This website might help your partition problems: 

[http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html](http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html)

e2retrieve might be particular help in this case. 

Keep us updated on any solutions you find

---

### Post by bilalsana on 2009-11-11
Boot from a live cd and then type this in the terminal:

sudo fsck -pcfv /dev/sda

replace 'sda' with correct hard disk id. it will scan all the drive for bad sectors and mark them bad so that they don't interfere in the future!

---

### Post by mivo on 2009-11-11
The thread was from early 2008. :) Long fixed since, thanks!

---

### Post by prshah on 2009-11-11
> **bilalsana said:**
> 
sudo fsck -pcfv /dev/sda

replace 'sda' with correct hard disk id. it will scan all the drive for bad sectors and mark them bad so that they don't interfere in the future!

Actually, you are attempting to scan the entire hard disk, and not just a partition, with that command and so it will fail. You will need to add a number to that "example" /dev/sda; eg /dev/sda9, so that it will indicate a PARTITION id, and not a "hard disk id".

---

