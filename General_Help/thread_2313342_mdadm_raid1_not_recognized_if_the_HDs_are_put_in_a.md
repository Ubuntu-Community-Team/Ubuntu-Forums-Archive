---
title: "mdadm raid1 not recognized if the HDs are put in another bay"
date: 2016-02-11
forum: General Help
---

### Post by davidesweden on 2016-02-11
Hi,


I have created a RAID1 2TBx2 using mdadm in Ubuntu. The two drives are in an external bay (Icy Box IB-120StU3-Wh Dual Bay Docking Station) connected via USB to the laptop. Everything works fine.
However, If I put the two HDs in another bay (ORICO 4 Bay USB3.0 & eSATA Hard Drive Docking Station for 2.5/3.5 Inch HDD/SSD - [6648SUSJ3]), connected to the laptop via eSATA,  then the raid is not recognized. If I try to assemble the raid, it says there is no superblock.

The hard drives are visible, but it looks like the partitions are wrongly read. I attach two screenshots on how the application Disks sees the partition in the two hard drives. 
- For the working case (attachment "Raid1 recognized in USB bay", Disks recognizes the Linux raid partition correctly.
- for the non-working case (attachment "Raid1 no recognized in eSATA bay", Disks sees a Partition1 of 250GB and then non allocated space. How is it possible? (While creating the screenshot, I inserted just one 2TB hard drive to the Orico bay. The result is the same if I would insert both hard drives).

Can you please suggest what could I do?

Thank you in advance.
Regards,
David

---

### Post by davidesweden on 2016-02-16
Can you please suggest some check I can do on the partitions? I really cannot understand how changing bay can lead to Ubuntu not recognizing the partitions correctly.

---

