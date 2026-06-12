---
title: "Vista MFT trashed"
date: 2008-07-03
forum: General Help
---

### Post by Dave Higg on 2008-07-03
Hi

If this is a repeat i'm sorry.

i tried ubuntu 8.04 on a live disk and downloaded a file and saved the file to my c: drive which has vista ntfs on it.

when i run vista again and looked for the file the folder is corrupted an not accessible. Also system restore will not work because of error on disk.

every time i start the computer chkdsk runs but does not see a problem.

i have tried a few programs to repair the problem but none have worked. one of them (GetDataBack) was able to copy the folder and contents to another drive so the files are still there. is it the MFT that is trashed.

i have tried GetDataBack, SpinRite, Flobo Hard Disk Repair, Flobo HDD Bad Sector Repair, Test Disk and a couple of others but none have worked.

some help would be very appreciated

Cheers Dave

---

### Post by Dave Higg on 2008-07-03
Fixed at last.

Dont know what the cause of the problem was but it wasnt in the file system. I used a few different programs to check the MFT, Boot Sector and the complete file system and none could find a problem.

The solution was simple. I used Paragon Partition Manager Rescue Disk and deleted the folder. Fixed.

Cheers  Dave

---

