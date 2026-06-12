---
title: "Setting up Software Raid"
date: 2007-09-23
forum: General Help
---

### Post by codecomposer on 2007-09-23
Hi all,

Our video production center currently has several LaCie 2TB Ethernet Disks that we're using for networked video storage. These need to be backed up, either nightly or through a RAID, to an external LaCie 2TB drive.

Problem is, LaCie installs WinXP Embedded on these disks. When I couldn't find an acceptable solution with the Windows backup utility, we decided to install Ubuntu (7.04 desktop) on them. Previously, we had thought that LaCie had used a hardware RAID card to link 4 500GB SATAs together, with an extra drive for the operating system. Not the case.

LaCie is apparently using 4 500GB IDE drives hooked up through the two IDE slots/buses on the motherboard. The operating system sits on the first drive in a separate partition. The remainder of space on the first drive is part of a RAID 0 with the other 3 drives.

My problem is this: How can I setup this system where the OS is part of the first drive, and then use the remainder of the first drive with the other 3 drives to create a software RAID? It's my understanding that running two IDE drives on the same IDE bus in a software RAID is a bad idea performance wise, but it's already fast enough for us.

Do I need to install Ubuntu onto an external drive? Or can I do it this way?

After that, the data needs to be in a RAID 1 with the external 2TB drive (a RAID 10, I guess), but that's something I can figure out on my own.

Thanks in advance.

---

### Post by kidders on 2007-09-24
> **codecomposer said:**
> It's my understanding that running two IDE drives on the same IDE bus in a software RAID is a bad idea performance wiseIt's a bad idea where an alternative exists, I suppose.

> **codecomposer said:**
>  Do I need to install Ubuntu onto an external drive?No. You can set RAID up any way you like, really. The only major concern is how the result will perform.

---

