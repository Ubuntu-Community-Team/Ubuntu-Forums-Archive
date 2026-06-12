---
title: "CloneZilla failed to backup"
date: 2016-04-28
forum: General Help
---

### Post by kakashi_12 on 2016-04-28
Tried to backup Ubuntu to CloneZilla. No problems in the past, recently.
here is the error message:

extfsclone.c: FS contains a file system with errors.
Partclone fail, please check /var/log/partclone.log !
Checking the disk space ...

I tried to locate this file in this directory (both on the internal and external drive), but the file does not exist. I have plenty of disk space on the external. About 340 GB.

---

### Post by ajgreeny on 2016-04-28
I wonder if clonezilla is baulking at an error in the filesystem you are trying to backup?

Try booting to a live system and run ```
sudo e2fsck /dev/sdx#
``` on the partition or partitions you are trying to clone (edit that sdx# to the correct partition) to see if any problems are noted.

---

### Post by RobGoss on 2016-04-28
How are you booting **Clonezilla **from a **USB** or **Disk**, you might want to download a fresh copy and see how that works, when I use Clonezilla I get a few error messages but strangely enough it always manages to make a complete backup for me

---

### Post by kakashi_12 on 2016-04-29
Results:

Ubuntu: clean.
x# of files. x# of blocks.

---

### Post by kakashi_12 on 2016-04-29
I was able to successfully clone my other HDD which has Windows 7 and Windows XP partitions on it. No problem. But with the other HDD that has Linux, is where it fails. I selected the option this time to "Check file system before backing up" within CloneZilla. And it tells me there are bad sectors. Won't tell me how many though. What if it's just 1 bad sector, that should still allow me to work with what I have. And then it actually continued to backup, got about 85% of the way, then said some other error (maybe the same thing about sectors), and then gave me the option to "Save as much I can" which I chose that option. And then it quit at that point. So it never got to 100%. So not sure if this partial backup is actually restorable or not.

---

### Post by kakashi_12 on 2016-04-29
Ran HD Tune. It found only 5 bad sectors. 0.2% damaged blocks.

---

### Post by kakashi_12 on 2016-05-01
Ok, so now I need help please. I am trying to repair the bad sectors with the same cmd recommended above with a different option.
```
sudo e2fsck /dev/sdb -p
```
Also tried sdb1 (so it would get just the ubuntu partition without the swap partition. But it does not repair the drive.

When I do the option with sdb, I see this output:
/dev/sdb is in use.
e2fsck: Cannot continue, aborting.

When I do the option with sdb1, I see this output:
Ubuntu: clean, 1154705/18317312 files, 8090368/73241856 blocks

But the drive is not in use, because I am booted to a Live CD. Do I need to mount or unmount it somehow?
OR is there another free program/cmd that I can use? Windows doesn't recognize it (through My Computer) so that is out. And I don't think Disk Management offers the option to repair sectors.

---

### Post by kakashi_12 on 2016-08-02
Switched from Ubuntu to Mint. Problem solved. CloneZilla now backs up the partition without issue or error.

---

### Post by howefield on 2016-08-02
> **kakashi_12 said:**
> ...Partclone fail, please check /var/log/partclone.log !
Checking the disk space ...

I tried to locate this file in this directory (both on the internal and external drive), but the file does not exist. I have plenty of disk space on the external. About 340 GB.

Just for info, the log file will be in RAM. When Clonezilla is done, select the option to drop to a command prompt and do..

```
cat /var/log/partclone.log
```

or if it is too much info and scrolls off the screen, pipe it to less to view a screen at a time.

```
cat /var/log/partclone.log | less
``` 

then a sudo reboot when you are donee.

---

