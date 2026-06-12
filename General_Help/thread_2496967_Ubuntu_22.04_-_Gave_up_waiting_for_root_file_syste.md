---
title: "Ubuntu 22.04 - Gave up waiting for root file system device."
date: 2024-04-18
forum: General Help
---

### Post by badozier on 2024-04-18
Just got home from work, turned on the laptop, first thing I saw was a popup for updating the system, so I clicked to update the system then walked away. Cam right back and this is what I saw.
----------------------------------------------------------------------
**Message Reads: Ubuntu 22.04 - Gave up waiting for root file system device.**


- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=(Long Series of Numbers and Letters) does not exit. Dropping to the shell
--------------------------------------------------------------------


I life boot from a usb, everything is there, everything is working.
Crazy thing is the /dev/sda identifies the partition completely via the command "sudo fdisk -l". 


The command df -h finds the partition as /dev/sda2 52% used.
Sudo fsck /dev/sda2 reads," /dev/sda2 is mounted."


I check /etc/fstab and find the UUID is correct there, then I check /media and find the partition with the same UUID there and find my partition there in working order, but only in read mode.


"I so like to get it out of read mode so I can back everything to my NAS."


What can be done to get everything back in working order?

---

### Post by TheFu on 2024-04-18
If the drive is in read-only mode, you can mount it and backup all the data on it still.

From the information provided (mostly description which can be misinterpreted), it sounds like some logical or physical issue with some part of the storage subsystem.  That could be a failing cable or a failing HDD or a corrupted partition table.  It could be multiple things too.  Cannot tell from the data provided.  

Step 1: backup anything you don't want to lose.  If you can't connect to your NAS, get the data somewhere else. Nothing is more important.

Step 2: take the few ideas I've listed and run commands to gather information.  **gdisk**, **fdisk**, **blkid**, fstab and other config files, and run a short SMART test (smartctl with some options). All these things can be run from a Try Ubuntu environment.

We like/need to see text output showing what is claimed.  It isn't that we don't believe you, but sometimes data gets misinterpreted both by you and by some of us, so having multiple eyes look it over is the best way to figure out the more correct answer from what we see.

If all the questions aren't answered that have been asked, I'll just wait.

---

### Post by userubu64 on 2024-06-19
> **TheFu said:**
> If the drive is in read-only mode, you can mount it and backup all the data on it still.

From the information provided (mostly description which can be misinterpreted), it sounds like some logical or physical issue with some part of the storage subsystem. That could be a failing cable or a failing HDD or a corrupted partition table. It could be multiple things too. Cannot tell from the data provided.

Step 1: backup anything you don't want to lose. If you can't connect to your NAS, get the data somewhere else. Nothing is more important.

Step 2: take the few ideas I've listed and run commands to gather information. **gdisk**, **fdisk**, **blkid**, fstab and other config files, and run a short SMART test (smartctl with some options). All these things can be run from a Try Ubuntu environment.

We like/need to see text output showing what is claimed. It isn't that we don't believe you, but sometimes data gets misinterpreted both by you and by some of us, so having multiple eyes look it over is the best way to figure out the more correct answer from what we see.

If all the questions aren't answered that have been asked, I'll just wait.
[COLOR=#000000]
I'm facing the same problem, could you help me? I created a thread [/COLOR][here]("https://ubuntuforums.org/showthread.php?t=2498563")

---

