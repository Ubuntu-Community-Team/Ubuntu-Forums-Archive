---
title: "filesystems remount by itself"
date: 2019-05-14
forum: General Help
---

### Post by lvm on 2019-05-14
I was rearranging the storage on a freshly installed 18.04 and was mounting and unmounting lots of filesystems. Several times filesystems I unmounted with 'umount /dev/sda1' were remounted back without any action on my part, and were quite persistent about it. I did check specifically - filesystems were indeed unmounted and came back, not failed to unmount:

umount /dev/sda1 - no errors
mount|grep sda1 - nothing
trying to do something with /dev/sda e.g. edit partition table - parted tells me that it is use and when I check again /dev/sda1 is now mounted at the same mountpoint

As far as I can remember all affected filesystems had entries in fstab but deleting these entries didn't resolve the issue, I had to reboot. Sometimes it got quite ugly e.g. I unmounted /dev/sda1, mounted /dev/sdb1 to the same mountpoint and it was silently replaced with /dev/sda1 - I nearly deleted some valuable data. Who is the culprit and how can I stop it from happening?

---

### Post by HermanAB on 2019-05-14
It is Gnome that very helpfully does it for you.

---

### Post by lvm on 2019-05-14
Sorry, forgot to tell that it was freshly installed *kubuntu* 18.04.

---

### Post by HermanAB on 2019-05-14
Well, then it is KDE that is helpfully doing it for you.  

The problem is that there is no single mechanism for handling system events - every desktop system does it differently.

---

### Post by lvm on 2019-05-15
Ok, what should I do to unmount filesystem permanently without any chance of it coming back? Ideally, what should I do to disable this annoying and dangerous feature?

---

### Post by oldfred on 2019-05-15
Are you mounting by using device like /dev/sda1. Whether any drive is sda, is determined by drive order set by UEFI/BIOS. And that can vary.
My system will put a USB flash drive as sda, changing every other drive.
That is why UUIDs became the standard or you can use labels which I now like to mount partition. I do label all partitions particularly those I only mount occasionally so I know what they are.

post this:
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

---

