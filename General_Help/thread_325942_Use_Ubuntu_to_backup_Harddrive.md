---
title: "Use Ubuntu to backup Harddrive?"
date: 2006-12-26
forum: General Help
---

### Post by HaiDozo on 2006-12-26
Hi,

I've never used Ubuntu before, or Linux for that matter.
My Windows machine got infected by a rootkit virus and I need to recover data from the HD with a non Windows system.

My question is; would I be able to use Ubuntu to access files from an internal and an external USB harddrive using NTFS and then burn those files to a DVD?

Thanks!

~HaiDozo

---

### Post by diepruis on 2006-12-26
IIRC you can read from NTFS disks, but not write to them, using Linux.

---

### Post by Rippey on 2006-12-26
yes you can, if you have 2 cd drives in your machine you wouldn't even have to install ubuntu.

---

### Post by tagra123 on 2006-12-26
> **HaiDozo said:**
> Hi,

I've never used Ubuntu before, or Linux for that matter.
My Windows machine got infected by a rootkit virus and I need to recover data from the HD with a non Windows system.

My question is; would I be able to use Ubuntu to access files from an internal and an external USB harddrive using NTFS and then burn those files to a DVD?

Thanks!

~HaiDozo


The live cd would work for that but for this sort of emergency try checking out sysrescuecd \.  Google for it.

Basically
 once the rescue cd has booted you'll want to type root than enter. Just press enter for the password.

Then,


I think youll need to use these same commands with ubuntu too.

mkdir /mnt/windrive

mount /dev/hdXx /mnt/windrive

mkdir /mnt/backup

mount /dev/sdXx /mnt/backup


use cp or rsync to copy.   

To get better help you can type man rsync.


The hdXx   (Large X will be some drive  a =1st ide master, b =1st ide slave, c - 2nd ide master, d - 2nd ide slave.

The small X will be a partition. -- its most likely 1 for a windows machine. 

More than likely the one you'll want is hda1.

The sdXx works the same way for the USB drive.

You'll figure it out rather quickly. Read over the sysrescue cd site and there are some helpful direction. Biggest thing for window users is knowing that hda1 is usually the same drive you are used to seeing as c:

Be patient and if you have another computer ask questions here. Someone will help and you wont lose your data.

I believe sysrescue cd now has full read write access to ntfs and is a little easier to use than the previous versions.

---

