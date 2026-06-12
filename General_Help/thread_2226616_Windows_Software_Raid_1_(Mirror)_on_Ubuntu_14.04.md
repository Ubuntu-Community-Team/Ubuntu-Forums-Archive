---
title: "Windows Software Raid 1 (Mirror) on Ubuntu 14.04"
date: 2014-05-28
forum: General Help
---

### Post by bizhat on 2014-05-28
Hi,

I dual boot between Ubuntu 14.04 and Windows 7.

On Windows 7, i have a Software Raid 1 (Mirror). That use two 1 TB Disks.

When i boot to Ubuntu 14.04, i can see the RAID 1 mirror as two disks, each with identical data.

Currently i used disks to mount of the RAID 1 disk in read only mode. I don't know if i delete data in one of these disk, it will cause problem when i boot to Windows and raid need to rebuild again (it take many hours to finish and slow my system performance during raid rebuild).

Is it safe to do write operation on Windows RAID 1 from ubuntu ? 

Thanks,

Santhosh

---

### Post by TheFu on 2014-05-28
No, it is not safe.
Do NOT access Windows SW-RAID disks from Linux. That is a road to corrupted data.

---

### Post by bizhat on 2014-05-29
> **TheFu said:**
> No, it is not safe.
Do NOT access Windows SW-RAID disks from Linux. That is a road to corrupted data.

Thanks for the reply.

---

