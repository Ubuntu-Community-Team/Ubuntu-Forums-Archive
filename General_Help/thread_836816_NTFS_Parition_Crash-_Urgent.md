---
title: "NTFS Parition Crash- Urgent"
date: 2008-06-21
forum: General Help
---

### Post by ReyCazador on 2008-06-21
I tried accessing a file on an XP ntfs partition from Hardy. When it got stuck I manually rebooted the system. This happened twice. After 2 failures I tried to boot XP which gave me a blue screen message. So I tried opening those partitions from Hardy that also failed with the following error
[IMG]http://i202.photobucket.com/albums/aa319/ReyCazador/error.jpg[/IMG]

This is big trouble for me. At the very least I have to recover the data on those ntfs partitions. Force mounting as given in that error message didn't work at least I couldn't do it is there some other way to mount/force mount the drive. Please help this problem is URGent

---

### Post by jeremy1138 on 2008-06-21
can you hit F8 at startup and get windows to start in safe mode?

---

### Post by cariboo on 2008-06-21
If you've got a proper Windows install disk and not a restore cd, you can boot in to a recovery console and tell it to run chkdsk on the next boot.

Jim

---

### Post by prshah on 2008-06-21
> **ReyCazador said:**
> I tried accessing a file on an XP ntfs partition from Hardy. When it got stuck I manually rebooted the system.
 is there some other way to mount/force mount the drive. Please help this problem is URGent

Boot into safe mode with command prompt, and run "chkdsk /f" on your affected drives, eg```
chkdsk/f c:
``` Some drives may require a reboot to be checked.

---

### Post by jeremy1138 on 2008-06-21
> **cariboo907 said:**
> If you've got a proper Windows install disk and not a restore cd, you can boot in to a recovery console and tell it to run chkdsk on the next boot.

Jim

That's what I think needs to happen somehow...  That windows partition thinks it has an error so the partition is locked until it scans the disk.  Doesn't it normally do that automatically after windows doesn't start correctly for whatever reason?

---

### Post by ReyCazador on 2008-06-21
> **prshah said:**
> Boot into safe mode with command prompt, and run "chkdsk /f" on your affected drives, eg```
chkdsk/f c:
``` Some drives may require a reboot to be checked.

Since, at present I do not have the installation disc,  I will try this. Thank you very much.

---

### Post by Habbit on 2008-06-21
If you cannot boot into Windows and you need as much data as you can get right now, do the following:
DISCLAIMER: this command will **clear the NTFS journal**, making it impossible for a later Windows' CHKDSK to just "replay" it (as fsck.ext3 would do, for example), so you will need a lengthy, full check, not to mention the possibility of leaving the FS structures in an inconsistent state and losing whole folders:
```
# mount -t ntfs-3g /dev/sda1 /media/disk -o force
```
Only do this if you're desperate and willing to take the aforementioned risks and the additional one that your computer might catch on fire or trigger a nuclear explosion...

---

