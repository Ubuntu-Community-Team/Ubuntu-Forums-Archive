---
title: "All versions of Ubuntu have become very sluggish during file transfers"
date: 2013-10-26
forum: General Help
---

### Post by shaneburton on 2013-10-26
Hey guys I am having a heck of a time with the 13.x code base and usability during file transfers.  I have tried just about every distro under the sun and ALL of them have the same issue.  Anytime I am transferring a large amount of data, the entire system becomes almost unusable.


[LIST=1]
[*]All distros (Ubuntu, Kubuntu, Lubuntu, Kali, etc.) have this issue and it doesn't matter what arch (x86 or x64)
[*]The computer doesn't seem to matter either unless it is something specific to Dell's.  I have an XPS Studio 1558 Laptop and an XPS 435T/9000 Desktop and they both have the same issue.
[/LIST]

I am formatting the HD as one partition so I am not sure if that makes a difference or not.  Any help would be greatly appreciated.

Thanks!

---

### Post by 3rdalbum on 2013-10-27
Writing data to an NTFS-formatted drive is CPU-bound, everyone gets poor performance during that.

Also, if one or both disks are encrypted, that is also CPU-bound and therefore a bit slow.

If neither of those are applicable maybe someone else might be able to help.

---

### Post by shaneburton on 2013-10-27
Definately not using NTFS or encryption.  All of my fs are ext4.  It is just really odd.  I never had this problem in the 12.x versions.  Could it be some odd write cache issue on the disks.  I notice when they boot, it assumes write cache.  I could be way off base, just throwing something out.

---

