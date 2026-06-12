---
title: "fix my hard drives!"
date: 2007-12-07
forum: General Help
---

### Post by psychofish on 2007-12-07
I got a few new hard drives, tried to mount them in Ubuntu (7.10) and it seemed to work fine for a while and now it's all screwy.

Exact details:
- I got a new 320GB SATA drive to replace an old 300GB non-SATA drive. I cloned the information onto the new drive, but left the old drive in the system anyway in case I ever need more storage (and it would be good as a backup). This is NOT my primary drive-- this is just the data one, storing music, photos etc. It is formatted ntfs so my Windows partition can access it.
- The old drive was mounted as /media/sdb1. I had the new one mount to the same location so all my paths stay the same. I just changed the uuid of the drive to the new one.
- Meanwhile, because I have an external drive at /dev/sdc, the old drive became /dev/sdd. I know this because I ran the "fdisk -l" command which told me which disks were where.

Simple enough right? It worked fine for a couple weeks, until suddenly everything blew up.

I don't know if it's because of the slew of recent updates to the system (to tell you the truth I didn't pay too close attention to it) but on my last boot all my disks were moved around! Running "fdisk -l" now puts my external drive at /dev/sdd, my old drive at /dev/sda, my new drive at /dev/sdc. WHAT?? I have most my drives mounted by UUID so this is not so bad, but for the ones that are NOT, this was a problem. Also, it would be nice to have the /media mount points match to the /dev designations so it's not confusing.

Also, as a side effect-- or perhaps a separate issue I don't know-- the entries on computer:/// and the Places menu is completely messed up. The volume names on my disks no longer point to the correct mount points and it also looks like some mounts aren't even showing up. Since this menu is separate from the fstab is there a way to change this? Is something else conflicting? What am I overlooking in the drive mounting process? Also how do I find the UUID for drives where I'm missing it?

---

### Post by cdenley on 2007-12-07
You can determine the uuid of all your paritions by running "ls -l /dev/disk/by-uuid". Have you made any changes to your bios settings? My system seems to detect drives in the same order as the bios boot order.

---

### Post by psychofish on 2007-12-14
Ahh-- that would explain it-- I had drives on IDE0 and IDE2 previously, and my new drive got inserted at IDE1, between the other two.

---

