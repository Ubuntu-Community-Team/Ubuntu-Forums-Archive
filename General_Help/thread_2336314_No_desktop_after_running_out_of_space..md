---
title: "No desktop after running out of space."
date: 2016-09-07
forum: General Help
---

### Post by Franz_Ziereis on 2016-09-07
I was using Photorec to recover files from a thumb drive with the destination being a folder on my computer.  I ran out of space on my HDD and I went to delete the recovery folders that had been created.  The permissions were locked on those to folders and so I sent the unprotected folder they were in to the trash and deleted that.  I didn't recover the space though (over 1 gb).  I rebooted and, beyond my LUKS login screen, all I get is a dark, blank screen.  I booted into a live DVD and mounted the encrypted partition, I took some more files off and I ran fsck against the unmounted file system but when I look at properties for the partition it shows that I have 0 space left.  This even after removing a file over 100 mb.  I placed a forcefsck file in root and rebooted and let that run but all I get is a blank screen after entering my password.

Other behaviour:  I don't know if this is normal or not but when I was in the live DVD and tried to copy/paste a file to a thumb drive, it wouldn't let me do it unless I was root.  I typically will do a gksudo nautilus when it comes to dealing with these types of things and I had to open nautilus in root to copy/paste as well as cut the larger file to the thumb drive.  When I had the initial problem of running out of space, I didn't have enough space to allow a gksudo opening of nautilus to delete the two protected Photorec folders which prompted me to delete the unprotected folder they were in.

I'm running Ubuntu 14.04 dual booted with XP.  Ubuntu is entirely encrypted and /boot is on a thumb drive.

This problem is beyond my experience and I would appreciate any help.  Thank you.

---

### Post by Franz_Ziereis on 2016-09-07
Well, I moved even more files; over a 1 GB, off the drive and it finally started to register free space again and I was able to boot.  When I think about it now, one of the Photorec folders was over a GB when I checked it but I'm pretty certain I didn't even have that much free space on the partition to accommodate that so I don't see how that could have been.  I guess my only concern now is that my disk usage isn't really what's purported or reported by the system.  Is there any way to check that?

Curious to read several threads this morning involving zero disk space screwing up people's boots.  In my case though it wasn't a case of too many kernals on /boot as that's on a removable thumb and I keep only two at a time and I run BB and Tweak on a regular basis.

---

### Post by ian-weisser on 2016-09-07
What disk space is reported by the system?
```
df
df -i
```

---

### Post by Franz_Ziereis on 2016-09-07
:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             1530836        4   1530832   1% /dev
tmpfs             308872     1344    307528   1% /run
/dev/dm-0       25674620 23189612   1157752  96% /
none                   4        0         4   0% /sys/fs/cgroup
none                5120        0      5120   0% /run/lock
none             1544340      288   1544052   1% /run/shm
none              102400       44    102356   1% /run/user
/dev/sdb1        7561384  7047980    106264  99% /boot

:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            207608    591  207017    1% /dev
tmpfs           214361    627  213734    1% /run
/dev/dm-0      1640160 286045 1354115   18% /
none            214361      2  214359    1% /sys/fs/cgroup
none            214361      3  214358    1% /run/lock
none            214361      6  214355    1% /run/shm
none            214361     28  214333    1% /run/user
/dev/sdb1       488640    338  488302    1% /boot

What does that tell you?  Like I said, the whole incident was curious.  I'm sure I had less than 1 gb free but the Photorec folder was reported at over 1 gb.  When I trashed the folder that the Photorec folder was in and emptied the trash, it didn't give me back any space.  Moving an one hundred or so mb file, while in a live DVD, wasn't good enough to start freeing any space.

---

### Post by Franz_Ziereis on 2016-09-07
One thing I've often wondered about is the difference I see in System Monitor between "Free" (2.5 GB) and "Available" (1.2 GB) space.  From my reading, and if I understand it correctly, this difference between "free" and "available" is because a certain amount of space is reserved exclusively for the system to write to important files and other duties and thereby ensure that the system doesn't come up short for those uses even if I fill up all my available space. Is this correct?

---

### Post by ian-weisser on 2016-09-07
> **Franz_Ziereis said:**
> :~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/dm-0       25674620 23189612   1157752  **96% /**
/dev/sdb1        7561384  7047980    106264  **99% /boot**
[...]
What does that tell you?

I see two interrelated problems.
The first problem is that your root (/) filesystem partition is out of space.
The second problem is that your /boot partition is full.

Fix the first problem by moving data to an external device, or by deleting it. You are already doing this, I see.
The first problem will prevent your desktop from loading, as you have discovered.

The second problem is caused by accumulation of old kernels, as you already know.
Eventually, the second problem will break apt upgrades and installs, giving you lots of cryptic apt and dpkg errors and leaving your system vulnerable to published exploits.
Since you already know that problem, one assumes you also know how to prevent it.

---

### Post by Franz_Ziereis on 2016-09-07
I've got some files stored on /boot that I'm going to move off.  It's not actually old kernals taking up the space.  Thanks for your input.

---

