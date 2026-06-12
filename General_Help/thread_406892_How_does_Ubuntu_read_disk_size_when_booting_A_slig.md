---
title: "How does Ubuntu read disk size when booting? A slightly advanced question."
date: 2007-04-11
forum: General Help
---

### Post by Patrick K on 2007-04-11
How does Ubuntu (and i guess Linux in general) acquire size and usage data from hard disks and partitions during bootup? 

How does it know how large a drive/partition is, how much space is used, and how much free space is available?

---

### Post by pointone on 2007-04-11
The drive's partition table and the system BIOS should contain this information.

---

### Post by Patrick K on 2007-04-11
Anyone know if there is a Linux app that can read and display the partition table?

---

### Post by pointone on 2007-04-12
fdisk can do this, but please do be careful.

---

### Post by Patrick K on 2007-04-27
bump

---

### Post by Patrick K on 2007-04-29
bump

---

### Post by lukew on 2007-04-29
> **Patrick K said:**
> bump

I dont know why you are bumping twice; fdisk was the correct answer.

gparted could show you a graphical view if really required.

---

### Post by Patrick K on 2007-04-29
What I'm trying to find out is why Ubuntu shows 800 mb used on a partition that has 21.1GB used. All the Ubuntu disk utilities show this including an installed copy of GParted. GParted on the LiveCD and Windows show the correct used and free space. Ubuntu doesn't. Fdisk shows the partition size and location but not the used and free space. The property page in Nautilus shows the correct used space but the wrong free space (by over 20 GB). I'd like to know where Ubuntu gets it's free and used information since it is wrong.

Notice in the screenshot that GParted shows hda6 (Factoid) with 849MiB used. Notice also that the property page in Nautilus shows 21.1 GB used (which is correct). Yet Nautilus shows 35.3GB free. The partition is 36 GB in size. 

Perhaps I phrased the subject incorrectly but that's why I bumped.

---

### Post by Patrick K on 2007-05-02
bump

---

### Post by dcstar on 2007-05-02
> **Patrick K said:**
> What I'm trying to find out is why Ubuntu shows 800 mb used on a partition that has 21.1GB used. All the Ubuntu disk utilities show this including an installed copy of GParted. GParted on the LiveCD and Windows show the correct used and free space. Ubuntu doesn't. Fdisk shows the partition size and location but not the used and free space. The property page in Nautilus shows the correct used space but the wrong free space (by over 20 GB). I'd like to know where Ubuntu gets it's free and used information since it is wrong.

Notice in the screenshot that GParted shows hda6 (Factoid) with 849MiB used. Notice also that the property page in Nautilus shows 21.1 GB used (which is correct). Yet Nautilus shows 35.3GB free. The partition is 36 GB in size. 

Perhaps I phrased the subject incorrectly but that's why I bumped.

As far as I can remember (this is going back 20+ years now), the FAT filesystem directory structure has a place that is supposed to contain the amount of free space in the partition.

This number is supposed to be updated by the O/S whenever changes are made, and it exists so an application-O/S can **quickly** determine how much free space exists without having to check through every directory entry to see what is used (which could be very time and resource consuming).

If something is not updating this data correctly - or something is misreading it - then you will get discrepancies as described.

Doing a** fsck** is the first step to fixing anything like this.

---

