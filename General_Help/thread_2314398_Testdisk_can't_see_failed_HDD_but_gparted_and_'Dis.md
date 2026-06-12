---
title: "Testdisk can't see failed HDD but gparted and 'Disks' does"
date: 2016-02-20
forum: General Help
---

### Post by nknwn on 2016-02-20
Hi, Two disks have died in this Windows 8.1 Asus laptop!
This new 500GB disk, is less than 4 months old.
Here's what gparted sees:
[ATTACH=CONFIG]267403[/ATTACH]
and Disks:
[ATTACH=CONFIG]267404[/ATTACH]

The previous HDD was a different brand and it is was reported slightly differently in 'Disks' as there was a message: "this disk is about to fail" or words to that effect.

Testdisk and Photorec were able to see the previous failed disk, though I couldn't do much with them. I saved a couple of files that weren't worth saving.

The other difference is that I was able to run the Windows program ChkDsk on the old disk (it failed to save the disk and was painfully slow ~30hrs)  but this newer failed disk prevents Windows from booting from a live disk and Windows can't see it when I connect it externally via USB

Is there anything else I should be trying? It seems reasonable that if the partitions are intact and the disk is spinning and visible to gparted that I should be able to do something with it.

Thanks for reading,
nknwn

---

### Post by nknwn on 2016-02-21
OK, looks like this is a different Asus from last time. I'll just replace the disk. User files are unreachable. Laptop was dropped on to a a hard floor I'm informed

---

### Post by oldfred on 2016-02-21
If just Windows 8 or later with its always on hibernation of fast start up set, then Linux, gparted, Disks will not be able to "see" or mount the NTFS partitions. 

The NTFS Linux driver will not normally mount hibernated nor partitions needing chkdsk.
You may be able to mount manually in read only mode.

And some Windows drive fixes with chkdsk require more than one run, or as many as three. 
Or then 90 hours???

---

### Post by nknwn on 2016-02-24
Hi Oldfred, I gave it a shot and was able to mount /dev/sda2 in read only. After that I was able to boot Windows 8 recovery disk in order to run chkdsk. Unfortunately after an overnight run the ETA was still sitting at 999 hours. So now I've replaced the HDD and installed Windows 8.1 -- Here's hoping they have backed up their very important files.

---

