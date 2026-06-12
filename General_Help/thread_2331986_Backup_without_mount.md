---
title: "Backup without mount"
date: 2016-07-27
forum: General Help
---

### Post by ferdi_t on 2016-07-27
Hello!

I'm trying to fix my broken NAS and I've gotten to this point:

- the hdd is hooked up in my pc, which boots up thrugh usb
- the disk shows up with fdisk -l
- I am unable to mount the disk due to a bad superblock.

Fixing the superblock isn't my main priority atm, my first objective is to retrieve essential data. I have 32 gb of storage on a second flashdrive, not enough for a full image (which would consume around 1,5tb).

My question: is there any way to navigate to key folders, backup their contents, without actually mounting?

Thanks!

---

### Post by TheFu on 2016-07-28
It is always best to work on a mirror of the source disk. That means you want another 1.5TB disk and want to use **ddrescue** to copy all the bits to it from the failing disk(s). Working on the original is considered foolish in the data recovery world. Never harm the original is the rule.  

After you mirror the bits to the new disk, .... If the file system is supported, a tool like **testdisk** and **photorec** might be of use. But some NAS devices use non-standard file systems, so it might not work at all.

Also, when using fdisk, be certain the version you are using is new enough to support GPT disks.  Or just use **parted** or **gparted** instead.

---

