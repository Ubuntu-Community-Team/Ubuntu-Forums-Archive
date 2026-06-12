---
title: "Resize the / partition and make a new partition with the remaining space"
date: 2008-01-04
forum: General Help
---

### Post by rootware on 2008-01-04
Is that possible?And if it is, please tell me the name of the program who can do that. In GUI-mode, if possible.

---

### Post by ronmarley1 on 2008-01-04
Depending on the number of partitions you have, you should be able to do this.  I recommend the gParted LiveCD.
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by rootware on 2008-01-04
> **ronmarley1 said:**
> Depending on the number of partitions you have, you should be able to do this.  I recommend the gParted LiveCD.
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Here are my partitions:
> Device Boot Start End Blocks Id System
/dev/sda1 * 1 6375 51200000 7 HPFS/NTFS
/dev/sda2 6376 19457 105081165 83 Linux

---

### Post by stump138 on 2008-01-04
gparted has a nice gui which will allow to resize and see everything visually:) RonMarley1's tip about the gparted live cd is the way to go:)

---

### Post by ronmarley1 on 2008-01-04
> **rootware said:**
> Here are my partitions:

Looks to me like you are good to go.  Download the iso for the gParted LiveCD from the link I gave above.  Right click on the iso you download and burn it as a disk image.  Once it's done, reboot your computer with the CD inserted (make sure bios is set to boot from the CD first).  Once it boots and gParted loads, you will be able to resize the root partition and create another.

---

### Post by rootware on 2008-01-04
> **ronmarley1 said:**
> Looks to me like you are good to go.  Download the iso for the gParted LiveCD from the link I gave above.  Right click on the iso you download and burn it as a disk image.  Once it's done, reboot your computer with the CD inserted (make sure bios is set to boot from the CD first).  Once it boots and gParted loads, you will be able to resize the root partition and create another.

I thought it might be a problem because I have no free space left: I have only two partitions, one for Windows and one for Ubuntu and no free space...:confused:

---

### Post by lswest on 2008-01-04
you have to resize one, which would make more free space, which can be then formated into another partition.

---

### Post by ronmarley1 on 2008-01-04
> **lswest said:**
> you have to resize one, which would make more free space, which can be then formated into another partition.

Exactly correct.

---

### Post by ronmarley1 on 2008-01-04
Also, I assumed that the NTFS partition is for Windows XP.  If it is, you can use gParted to resize the Linux root partition or the XP partition and create the new one as the poster above pointed out.  If the NTFS is for Vista, I've read that you should use Vista's disk manager tool (or whatever it's called) to resize the NTFS partition.  If you do not, you can break Vista.  If you want to resize the Linux root partition, you can do that with gParted LiveCD and create the new partition from the freed space and that will not affect Vista.

---

