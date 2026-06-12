---
title: "Orphaned inode errors - can't be found in logs"
date: 2024-04-25
forum: General Help
---

### Post by fr33z0n3r on 2024-04-25
I just has my system lock up.  I REISUB'd it and upon boot,  I saw several lines of 'orphaned inodes' flash by real fast.  I am unable to locate any mention of 'inode' in any logs I've checked so far, including journalctl.

Does anyone know if/where this would be logged?

---

### Post by wyattwhiteeagle on 2024-04-25
> **fr33z0n3r said:**
> I just has my system lock up.  I REISUB'd it and upon boot,  I saw several lines of 'orphaned inodes' flash by real fast.  I am unable to locate any mention of 'inode' in any logs I've checked so far, including journalctl.

Does anyone know if/where this would be logged?
You may need to reistall *buntu.
Are you currently using the LiveUSB?

---

### Post by TheFu on 2024-04-25
> **wyattwhiteeagle said:**
> You may need to reistall *buntu.
Are you currently using the LiveUSB?

NO!

inodes are controlled by the file system.  You should run the file system checker for the specific file system type.  Most native linux file systems have a tool just for this.  Depending on which file system is the issue.  I'll assume you can't get to the grub Advanced Boot menu and go into "rescue" mode.  If you could, a menu should be displayed that has "file system check" or "check all file systems" ... something like that.  Choose it.

If you can't get into the grub Advanced Boot menu, boot from a live/install Linux - preferably the same release number as installed, but don't worry if the DE is different.  Go into the "Try Ubuntu/Lubuntu/Xubuntu/Kubuntu" option. That will boot into a GUI using the ISO file on the flash drive.  Then you can open a terminal, find the file system devices (usually something like /dev/sda1 ... but don't wildly just put in devices. That can make it worse.  If you need help determining which file systems exist, run 
```
sudo fdisk -l   # <---- that's a lower-case L
```
Then post the results back here with forum code tags.  Also, we never need to see any "loop" devices. They aren't real storage, so best to delete those from the output to prevent hassles for people trying to help.

To manually run the file system checker ... 
```
sudo fsck -t {the file system type}  {the device file name}
```
For example, 
```
sudo fsck   -t     ext4    /dev/sdz1
```

Ask if you need more details.  BTRFS and ZFS don't use fsck. Don't try.

Reinstalling would be the last option, but we are long away from that at this point.  Heck, it could be a failing HDD, so reinstalling won't fix anything.

---

### Post by wyattwhiteeagle on 2024-04-25
> **fr33z0n3r said:**
> I just has my system lock up.  I REISUB'd it and upon boot,  I saw several lines of 'orphaned inodes' flash by real fast.  I am unable to locate any mention of 'inode' in any logs I've checked so far, including journalctl.

Does anyone know if/where this would be logged?

Please excuse my lack of understanding but...
What is REISUB'd?
I assume LiveUSB was meant based on the OP's grammar of the first sentence.

---

### Post by deadflowr on 2024-04-25
> What is REISUB'd?
It's a command sequence typically used to reboot a locked up system.
Fun read here: [https://askubuntu.com/a/926476](https://askubuntu.com/a/926476)

---

### Post by Holger_Gehrke on 2024-04-26
Each letter of 'REISUB' starts one part of a semi-controlled shutdown. The 'S' does a sync - basically writing out any unwritten pages of the cache, the 'U' unmounts all file systems, and the 'B' does a reboot. You should really give each function a few seconds to work, but that goes double for sync. If you do the unmount before the sync is completely done, some damage to the file system is to be expected. As TheFu already said, boot from a live system and do a file system check (fsck). That should get the file system back into a consistent state (especially for a journaled file system), but you might still encounter some corruption.

Holger

---

### Post by fr33z0n3r on 2024-04-27
I did a fsck from a usb,  and it found no issues.  I will bear in mind the point about the recommended delay in REISUB.  Maybe that caused my issue. 

This happened on a brand new NVMe drive.  So quite disappointing if the storage was the issue.  Not sure if my REISUB and subsequent inode issue can validate that either way

---

