---
title: "Reconfigure RAID and partition layout after new hardware swap"
date: 2016-12-29
forum: General Help
---

### Post by alldunn2 on 2016-12-29
I have a personal home media server currently running Ubuntu server 14.04.  I just recently swapped motherboard, CPU, and RAM for newer parts.  I had a mirrored array (fake raid) from the previous motherboard with the / and /home (separate partitions).  Now that I have the new motherboard, the system boots fine, but in AHCI mode.  I obviously need to reconfigure RAID, but I also want to combine my partitions on this array to take advantage of extra space.  I was thinking of doing a tar.gz backup of both partitions, reconfigure RAID, format, and then restore to one big / partition.  Does anyone have any better suggestions on how to accomplish this method quickly, and more important, successfully?  Thanks for any input.

---

### Post by TheFu on 2016-12-30
Welcome to the forums.

a) don't use fakeRAID. It has all the problems of HW-RAID and none of the flexibility of SW-RAID.

b) use file-based backups - rsync or your normal, daily, backup tool.  tar is for 20MB backups, not 20GB backups. There are 50 better options and have been 50 better options than tar for 15 yrs. rsync will be the fastest if you don't have a backup already.

c) RAID, LVM, Partitioning doesn't matter as long as the files "appear" to be in the correct locations at boot.

FakeRAID is a complete waste except for 2 purpose. To have slowRAID and HW-dependencies.  Crazy.  Use SW-RAID if you want HA. Use quality HW-RAID (like LSI cards) if you want performance.  None of these remove the need for daily, automatic, versioned, backups.  RAID solves 1 or 2 issues. Backups solves 1000+ issues.

So some reading on FakeRAID.

---

