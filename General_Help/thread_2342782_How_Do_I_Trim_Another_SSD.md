---
title: "How Do I Trim Another SSD?"
date: 2016-11-09
forum: General Help
---

### Post by ThePowerpuffGirls on 2016-11-09
I have another SSD hooked up via SATA, I deleted all the data and formatted it to EXT for. Is there a way to clear all the blocks and set it back to default factory settings?
I've used Bleachbit, but was able to recover some files, less than 20.

What is the best way to format a drive, or should I use BleachBit?
Is there a way to wipe or clear thew blocks faster?

---

### Post by oldrocker99 on 2016-11-09
Here's the best page on how to set up fstrim to work automatically as a cron job on more than one drive:[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html).

---

### Post by howefield on 2016-11-10
> **ThePowerpuffGirls said:**
> ... Is there a way to clear all the blocks and set it back to default factory settings?

What I do is..

```
sudo hdparm --user-master u --security-set-pass Eins /dev/sdX && sudo time hdparm --user-master u --security-erase Eins /dev/sdX
```

where X is the drive letter.

---

### Post by ThePowerpuffGirls on 2016-11-13
I get:

```

/dev/sda1:
 Issuing SECURITY_SET_PASS command, password="Eins", user=user, mode=high
SECURITY_SET_PASS: Input/output error

```

---

### Post by kingneutron on 2016-12-01
--See this for more info:
[https://wiki.archlinux.org/index.php/Solid_State_Drives/Memory_cell_clearing](https://wiki.archlinux.org/index.php/Solid_State_Drives/Memory_cell_clearing)

[http://www.linux-magazine.com/Online/Features/Fixing-Disks-with-Parted-Magic](http://www.linux-magazine.com/Online/Features/Fixing-Disks-with-Parted-Magic)
^ Search page for "secure erase"

[https://www.thomas-krenn.com/en/wiki/SSD_Secure_Erase](https://www.thomas-krenn.com/en/wiki/SSD_Secure_Erase)



--If the Linux way doesn't work for you, try going to the drive manufacturer's website and see if they have a utility available (will probably be Win-based.)

---

### Post by kpatz on 2016-12-01
If it's formatted to ext4 the weekly cron job will trim it automatically.

Or just run:```
sudo /sbin/fstrim mountpoint
```
replace mountpoint with where the partition of the new drive is mounted.

---

### Post by QIII on 2016-12-01
fstrim does not do a memory cell factory reset.

fstrim relies on some communication between the OS and the drive firmware to decide which erasure blocks can be cleared.  Say you take an SSD from one machine and put it in another.  fstrim will not necessarily completely clear the drive.

You have to the full factory reset.

The instructions given for Arch are dead simple and complete.

---

### Post by mc4man on 2016-12-01
The thread title & question's intent aren't the same, Op wanted to do a secure erase. The command given was proper though it looks like Op used on a partition instead of the drive (sda1 vs. sda
More complete instructions would be here 
[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

