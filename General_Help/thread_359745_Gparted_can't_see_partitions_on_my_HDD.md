---
title: "Gparted can't see partitions on my HDD"
date: 2007-02-12
forum: General Help
---

### Post by markr on 2007-02-12
Hi,

I have a 60 gig HDD with NTFS (WinXP), ext3 (shared) partition, ext3 (PCLinuxOS), ext3 (Ubuntu 6.10) and a Swap.

I was planning on ditching PCLinuxOS in favour of Kubuntu herd3, but when I run gParted (From Ubuntu and also Ubuntu LiveCD), it tells me I have a 60gig unallocated drive!!

The last thing I did with my partitions was shrink the Ubuntu 6.10 to fit the new PCLinuxOS ext3 partition.  My Windows and Ubunto OS's work perfectly, I can do a df -k and the parititions are accurately reported.

I'm very confused!!  Any thoughts.

Mark.

---

### Post by FenrisAbraxas on 2007-02-12
> **markr said:**
> Hi,

I have a 60 gig HDD with NTFS (WinXP), ext3 (shared) partition, ext3 (PCLinuxOS), ext3 (Ubuntu 6.10) and a Swap.

I was planning on ditching PCLinuxOS in favour of Kubuntu herd3, but when I run gParted (From Ubuntu and also Ubuntu LiveCD), it tells me I have a 60gig unallocated drive!!

The last thing I did with my partitions was shrink the Ubuntu 6.10 to fit the new PCLinuxOS ext3 partition.  My Windows and Ubunto OS's work perfectly, I can do a df -k and the parititions are accurately reported.

I'm very confused!!  Any thoughts.

Mark.

Hmmm have you tried to use fdisk in the console? is not hard to partition a HD using fdisk :P

---

