---
title: "Data recovery on bad hard drive?"
date: 2007-07-27
forum: General Help
---

### Post by 67GTA on 2007-07-27
I have noticed several problems with Ubuntu locking up and several errors that made no sense for a couple of days. Tonight I got a grub error while rebooting and a failed fsck check confirmed bad blocks on sda4(Ubuntu partition). Windows will not run very well either. I ran a disk check in XP and got a couple of disk errors also. I ran the live cd and gparted could not read the sda4 file system, so I couldn't mount it to pull anything off the partition. Reinstalling on a new HD is no problem because I keep my home folder backed up pretty regular on cd/dvd. I really need to get some pictures that I recently loaded onto sda4 of our 4 month old daughter. The rest were backed up. How can I get them off the HD?

---

### Post by merlinus on 2007-07-27
This may help:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

-merlin

---

### Post by HermanAB on 2007-07-27
One word: Knoppix.

Cheers,

Herman

---

### Post by 67GTA on 2007-07-27
I couldn't get Firefox to open, so I ran fsck with the Ubuntu live cd. It ran long enough to fix about 283 disk errors. I was able to boot into sda4 with Super Grub Disk and copy my picture folder to the Windows partition, and burn that to cd using XP. Windows is barely running. When I try to open IE the computer reboots :( My Ubuntu partition is FUBAR. I had to boot into recovery mode to move the folder. As soon as I get it running again, I will burn me a Sysresccd cd. It has everything I needed tonight. Thanks for the help.

---

### Post by HermanAB on 2007-07-27
What kind of file system were you using?  FAT or Ext2?

---

### Post by 67GTA on 2007-07-27
My Ubuntu partition is (was)ext3.

---

### Post by HermanAB on 2007-07-27
Something to ponder:
Ext3 is very robust.  If it screws up, then it usually indicates a serious hardware problem, which is usually the disk itself.

---

### Post by UniRecovery on 2007-07-28
BE careful, very careful...dont try the recovery disks, you may have some  "bad sector" damage, which can easily deteriorate into a physical damage on the head (read/write arm). If you want your photos reapir the sectors witha  software that is not windows based,m the software would have to be a DOS based software to avoiud any overloading , which may easily cost you the data.
Good luck

---

