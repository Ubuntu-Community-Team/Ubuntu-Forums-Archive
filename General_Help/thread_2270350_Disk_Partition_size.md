---
title: "Disk Partition size"
date: 2015-03-22
forum: General Help
---

### Post by alexaron17 on 2015-03-22
Hi all
Recently I installed Ubuntu 14.04 LTS alongside Windows 8.1 in a dual boot. After a while, I wanted to remove it and so I decided to restore my computer. This gave me a big issue with the MBR and took a large number of steps to boot into Windows again. During the issue, I used Ubuntu Live and efibootmgr to remove Linux partitions. I have now fixed the issue, but it says that my HDD still only has 451GB available (it is a 1TB HDD) from when I halved the space for Ubuntu.
How do I restore the space of the HDD?
Regards
Alex

---

### Post by leclerc65 on 2015-03-22
Windows does not recognize anything Linux, so you have to format the partition as NTFS.
I use Gparted (free) in Pmagic (not free) on CD to execute such a task.

---

### Post by alexaron17 on 2015-03-22
Okay, will download Gparted now and give it a go.

---

### Post by ajgreeny on 2015-03-22
If you haven't already downloaded gparted live to do this, you can use gparted from the live ubuntu system you already have used; there is no need to download anything else for gparted.

---

