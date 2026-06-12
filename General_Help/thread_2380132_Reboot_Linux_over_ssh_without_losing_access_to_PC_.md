---
title: "Reboot Linux over ssh without losing access to PC (mount issue)"
date: 2017-12-13
forum: General Help
---

### Post by sylvus2 on 2017-12-13
Hi, Ubuntu had some problems with my main hard drive which is why the disk was mounted in read-only mode. I fixed those errors with fsck but I am still unable to remount the hard drive:

```
sudo mount -o remount,rw /dev/nvme1n1p2 / 
mount: cannot remount /dev/nvme1n1p2 read-write, is write-protected
```

I think the only solution might be to reboot. Unfortunately, I only have ssh access to the machine and nobody will be able to access the machine for the next 1-2 month. So if I reboot and it asks me some question on the boot screen, I will lose access. 

Question a) Can I somehow remount the disk without rebooting?
Question b) Can I safely reboot (for example disabling all prompts on startup)?


Here is what I tried:

```
sudo blockdev --setrw /dev/nvme1n1p2
sudo fsck.ext4 -y -f /dev/nvme1n1p2
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (8228173, counted=8303925).
Fix? yes
    
Free inodes count wrong (12707065, counted=12707147).
Fix? yes
    
    
/dev/nvme1n1p2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/nvme1n1p2: ***** REBOOT LINUX *****
/dev/nvme1n1p2: 801461/13508608 files (0.5% non-contiguous), 45725899/54029824 blocks
sudo mount -o remount,rw /dev/nvme1n1p2 /
mount: cannot remount /dev/nvme1n1p2 read-write, is write-protected
```
Note that this is the second time I ran fsck, the first time it fixed ALOT of errors. Proably introduced by also having windows using the same hard disk (mounting the ext4 under windows, windows itself is on a different disk).

---

### Post by Kirk Schnable on 2017-12-14
> **sylvus2 said:**
> Hi, Ubuntu had some problems with my main hard drive which is why the disk was mounted in read-only mode. I fixed those errors with fsck but I am still unable to remount the hard drive:

```
sudo mount -o remount,rw /dev/nvme1n1p2 / 
mount: cannot remount /dev/nvme1n1p2 read-write, is write-protected
```

[....]

Here is what I tried:

```
sudo blockdev --setrw /dev/nvme1n1p2
sudo fsck.ext4 -y -f /dev/nvme1n1p2
```
You ran FSCK on your root volume while the system was booted?  This is very much not advised.  You should never run FSCK on a mounted filesystem.

> **sylvus2 said:**
> Question a) Can I somehow remount the disk without rebooting?
What you've already tried is what I would suggest, (mount -o remount,rw).  The fact that it is not working is concerning, and may mean you have a serious corruption problem on the disk.


> **sylvus2 said:**
> Question b) Can I safely reboot (for example disabling all prompts on startup)?
Not likely.  There are prompts that could come from the BIOS that the operating system has no control over.  Also, since your disk might be corrupted, there is no guarantee that the boot loader is even still functional.


> **sylvus2 said:**
> Note that this is the second time I ran fsck, the first time it fixed ALOT of errors. Proably introduced by also having windows using the same hard disk (mounting the ext4 under windows, windows itself is on a different disk).
You had the filesystem mounted simultaneously on two operating systems?  Do you mean that this is a dual boot system and sometimes you boot into Windows, or is Windows always running somewhere (like in a VM) and mounting this ext4 volume?  If you are somehow using the filesystem in two places at once, it does not surprise me in the slightest that it became corrupted.


Sorry, but it sounds like you're in a bad situation here, I doubt the system will come back up if you reboot it.  I would also suggest getting yourself an IP KVM out there if you have 1-2 months swaths of time where the system can't be physically accessed, it will definitely save you some future headache especially if this is an important system.

---

### Post by HermanAB on 2017-12-14
Hmm, as is, the system isn't working anyway.  Why don't you just get yourself a different system?  A Digital Ocean droplet costs as little as $5 pm.

---

### Post by sylvus2 on 2017-12-14
Thanks for the answers. 
1. I can't get a different system because I need this specific hardware (GTX 1080 TI, ...) + the 4TB of data that is on an external hard disk attached to that PC. 
2. There are two internal M2SSDs. One has Windows the other has Ubuntu. I sometimes boot Windows and then use a program under windows to mount the ext4 Ubuntu partition and do some work on there. So yes that might be why it is (a bit) messed up. 
3. IP KVM sounds like a good idea. Will look into that when I get access. 
4. So what should I do now? I can not install anything because of the write protection. So reboot and hope for the best? I know it is a bad situation but even then I want to maximize my chances!

---

### Post by sylvus2 on 2017-12-15
Nobody has any advice on how to proceed?

---

### Post by Kirk Schnable on 2017-12-17
Really this is not a good situation here.  If I were in this position, I would find a way to get remote hands on site before I tried a reboot.  I think most likely you're not going to get out of this without at least a rescue environment, maybe a reinstall, possibly even replacing hardware if your NVME has gone bad and caused this corruption to begin with.

---

