---
title: "Existing Ubuntu Install - Adding Older Windows Install to Second Drive"
date: 2007-08-31
forum: General Help
---

### Post by mikessong on 2007-08-31
Hi,

I have been using Ubuntu for an while, and I enjoy it.  It was the only hard drive in my computer.

I have a harddive with Windows XP on it.  It's the original hard drive that came with the system, and its never been used.  I have to use it now to compile some stuff for Windows (yuck).

Anyway, this Windows hard drive was not in when I installed windows.  I bought a new hard drive, and Installed Ubuntu on it.

I'd like to add this existing hard drive as a secondary hard drive, and have Grub recognize it.  It doesn't seem to do it.  Ubuntu boots like normal, and it recognizes the the Windows hard drive.

How do I get Grub to recognize the Windows XP hard drive, when both are were installed separately?  If I had the computer boot to the Windows hard drive as the primary hard drive would it help?

I'm using Fiesty, 7.04.

Peace

---

### Post by confused57 on 2007-08-31
> **mikessong said:**
> Hi,

I have been using Ubuntu for an while, and I enjoy it.  It was the only hard drive in my computer.

I have a harddive with Windows XP on it.  It's the original hard drive that came with the system, and its never been used.  I have to use it now to compile some stuff for Windows (yuck).

Anyway, this Windows hard drive was not in when I installed windows.  I bought a new hard drive, and Installed Ubuntu on it.

I'd like to add this existing hard drive as a secondary hard drive, and have Grub recognize it.  It doesn't seem to do it.  Ubuntu boots like normal, and it recognizes the the Windows hard drive.

How do I get Grub to recognize the Windows XP hard drive, when both are were installed separately?  If I had the computer boot to the Windows hard drive as the primary hard drive would it help?

I'm using Fiesty, 7.04.

Peace

The Windows entry in this thread might work:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by merlinus on 2007-08-31
You will have to create an entry in /boot/grub/menu.lst along these lines, at the bottom of the file:

title        Microsoft Windows XP
root        (hd1,0)
savedefault
makeactive
chainloader    +1

-merlin

---

### Post by mikessong on 2007-08-31
I'm on the right track with your post.  It's helping.

Every time try I get a message saying the drive isn't founds, or doesn't exist or something like.

How do I know for sure the drive id hd1.

On the servers at work, I do something like
```
dmesg | grep '^hd.:'
```

These are sata drives, and it looks like they are ata3.00 for the primary Ubuntu drive and ata3.01 for the other drive.  Would that be correct?  I tried with first solution posted with hd0 and hd1.  The second one I tried as written.

Thanks for the help.  I feel like I'm so close.

---

### Post by merlinus on 2007-08-31
```

sudo fdisk -l

```

-merlin

---

### Post by confused57 on 2007-09-01
> **mikessong said:**
> I'm on the right track with your post.  It's helping.

Every time try I get a message saying the drive isn't founds, or doesn't exist or something like.

How do I know for sure the drive id hd1.

On the servers at work, I do something like
```
dmesg | grep '^hd.:'
```

These are sata drives, and it looks like they are ata3.00 for the primary Ubuntu drive and ata3.01 for the other drive.  Would that be correct?  I tried with first solution posted with hd0 and hd1.  The second one I tried as written.

Thanks for the help.  I feel like I'm so close.

You might want to check in bios if your Windows' drive is identified correctly.  Also, posting the command merlinus  mentioned would help:
```
sudo fdisk -l
```
-l is a lowercase "L"

The thread I gave you earlier should work  for SATA drives.

---

### Post by mikessong on 2007-09-01
This is what I'm trying right now, and it's so close:

```
title           Windows
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

It says invalid disk, press enter to try again.  Then it says no OS found, and freezes.

This is the output from fdisk -l:

```

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           7       56196   de  Dell Utility
/dev/sdb2   *           8        9118    73184107+   7  HPFS/NTFS
/dev/sdb3            9120        9725     4867695   db  CP/M / CTOS / ...

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    c  W95 FAT32 (LBA)

```

/dev/sdb is the Windows drive.  It's not mounted in Ubuntu, which is fine.

Again, thinks for the help.

---

### Post by mikessong on 2007-09-01
Ok, and I just checked the BIOS, and the second SATA drive was disabled.  I was only using one drive at a time before.  Now, when I booted to the windows drive, it went to some GUI disk checker thing.  It could be this:

/dev/sdb1               1           7       56196   de  Dell Utility

I guess I want it to go to this:

/dev/sdb2   *           8        9118    73184107+   7  HPFS/NTFS

The disk checker is running now.  I'm posting from another computer that I'm going to turn into a server.  Is there a way to get it to go into sdb2 and not sdb1, if that's even what it's doing?

---

### Post by merlinus on 2007-09-01
You might try changing (hd1,0) to hd(1,1).

hd1,0 is the dell recovery partition. windows is hd1,1, from what I can see.

-merlin

---

### Post by confused57 on 2007-09-01
> **mikessong said:**
> Ok, and I just checked the BIOS, and the second SATA drive was disabled.  I was only using one drive at a time before.  Now, when I booted to the windows drive, it went to some GUI disk checker thing.  It could be this:

/dev/sdb1               1           7       56196   de  Dell Utility

I guess I want it to go to this:

/dev/sdb2   *           8        9118    73184107+   7  HPFS/NTFS

The disk checker is running now.  I'm posting from another computer that I'm going to turn into a server.  Is there a way to get it to go into sdb2 and not sdb1, if that's even what it's doing?

I experienced the same problem when I installed Ubuntu on a Dell Dimension 4550, read down a little further in the link I gave you:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

As merlinus suggested, try using root (hd1,1)

---

