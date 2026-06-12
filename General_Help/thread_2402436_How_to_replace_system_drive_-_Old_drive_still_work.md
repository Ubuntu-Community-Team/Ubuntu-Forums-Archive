---
title: "How to replace system drive - Old drive still working, but struggling"
date: 2018-09-29
forum: General Help
---

### Post by dmbgo on 2018-09-29
Hi, I have an up to date installation of 64bit ubuntu desktop with 4 x 4tb sata drives and one x 2tb drive. The system and swap partitions are on the 2tb drive, which on several occasions has failed to boot until I run FSCK. I am worried that it will fail completely, and since it contains part of my 18tb LVM volume, I am risking a fairly substantial data loss.
I have purchased a 6tb hard drive with a view to replacing the system drive and perhaps somehow introducing some redundancy.
I'm not sure how to go about it though and I would be grateful for some help.

---

### Post by MoebusNet on 2018-09-30
I am NOT an expert on this; I haven't had to replace a system drive that also had part of an LVM system. However, what I have read on the forums leads me to believe that Clonezilla is a popular tool used to clone drives for this purpose. In essence, what you want to do is 1) back up all the files on your HDD. 2) Use Clonezilla to clone your HDD from old to new. Note that the new HDD must be of equal or larger size to the original HDD. If you want to investigate:

About Clonezilla - [https://www.clonezilla.org/](https://www.clonezilla.org/)

Clonezilla Tutorial - [https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

I believe this to be a good option, but you'll need to read up on it to make your decision. I hope this helps.

---

### Post by MoebusNet on 2018-09-30
I believe another option for failing HDDs is DDRescue:

DDRescue - [https://www.gnu.org/software/ddrescue/](https://www.gnu.org/software/ddrescue/)

DDRescue Manual - [https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html](https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)

---

