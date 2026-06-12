---
title: "Very Slow Boot Process"
date: 2007-03-21
forum: General Help
---

### Post by YumZ on 2007-03-21
When starting up Ubuntu 6.10, the graphical loader disappears and is replaced by a text one.  At this point it says "checking all file systems. . . fsck 1.39 (date here)."  It hangs there for 2-3 minutes, making the bootup process excruciatingly slow and annoying.  This happened when I was using Xubuntu 6.06 and it is happening again on a fresh install of Ubuntu 6.10.  Is there any way to fix this?

---

### Post by ComputerGuy56 on 2007-03-21
Are you shutting down your computer correctly or just killing the power? I once did that and it hung at that fsck thing.

---

### Post by YumZ on 2007-03-21
I've had to kill the power a couple times while using Windows due to complete system lockups.

---

### Post by ComputerGuy56 on 2007-03-21
If you have GRUB, run the memtest86 thing. I'm pretty new to Ubuntu but that's the best I could think of, sorry.

---

### Post by rsambuca on 2007-03-21
If you did an unplug, it could have messed things up with the drives, and thus the fsck.  Normally, ubuntu runs an fsck about every 25 mounts, so it shouldn't be doing it every time unless there is some other problem.

---

### Post by YumZ on 2007-03-21
I've never done an unplug so that can't be the problem.

---

### Post by rsambuca on 2007-03-22
Well, hard power-down during a lock up.  Same thing as the drives don't get to park.

---

### Post by tgalati4 on 2007-03-22
Drives are cheap.  It's a good idea to put Ubuntu on it's own drive so that the Windows infection won't spread.

---

### Post by rsambuca on 2007-03-22
> **tgalati4 said:**
> Drives are cheap.  It's a good idea to put Ubuntu on it's own drive so that the Windows infection won't spread.

I hope this statement is a joke.  Certainly not very helpful.

---

### Post by Peti29 on 2007-03-22
> **rsambuca said:**
> If you did an unplug, it could have messed things up with the drives, and thus the fsck.  Normally, ubuntu runs an fsck about every 25 mounts, so it shouldn't be doing it every time unless there is some other problem.

I have some auto-mounted FAT32 partitions and they seem to be checked every single time (however not so deep as my ext partition which is checked every 30 mounts).
So I also have this phenomena described in the OP which certainly increases booting time - I think it's less than 2-3 minutes though.

Edit:
It may have to do with fstab. I read in Ubuntu docs that > The sixth field, (fs_passno), is used by the fsck( 8 ) program to determine the order in which filesystem checks are done at reboot time.  The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2.
So if I understand it correctly only the root filesystem sould have 1, others should have 2 but in my fstab I see:
```
UUID=7E9B-D4EE  /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
```
I don't know what's the difference between 1 and 2...

---

### Post by mcduck on 2007-03-22
> **Peti29 said:**
> I have some auto-mounted FAT32 partitions and they seem to be checked every single time (however not so deep as my ext partition which is checked every 30 mounts).
So I also have this phenomena described in the OP which certainly increases booting time - I think it's less than 2-3 minutes though.

Edit:
It may have to do with fstab. I read in Ubuntu docs that 
So if I understand it correctly only the root filesystem sould have 1, others should have 2 but in my fstab I see:
```
UUID=7E9B-D4EE  /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
```
I don't know what's the difference between 1 and 2...

Like you said already, '1' should be used for / only, and '2' for any other partitions you wish to run fsck. But FAT is not able to store information about when it was last time checked so I'd recommend just changing the last number for your FAT partition to '0' to disable fsck for it completely. After that your system should boot correctly.

edit: I bet the original poster also has some FAT or NTFS partitions that are configured to run fsck, the same fix should work..

---

### Post by YumZ on 2007-03-22
Changing it to "0" worked perfectly.  Thank-you!

---

