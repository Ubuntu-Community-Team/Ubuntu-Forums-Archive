---
title: "Sata or sshd? (Solved)"
date: 2014-09-10
forum: General Help
---

### Post by ccct007 on 2014-09-10
How to tell if I have a sata harddrive or a sshd is my ?

---

### Post by QIII on 2014-09-10
SATA is a bus interface, not a type of drive.

Do you mean a mechanical drive (spinning platters) versus a solid state drive (SSD)?

---

### Post by ccct007 on 2014-09-11
sudo lshw -short -C disk
H/W path        Device      Class       Description
===================================================
/0/7/0.0.0      /dev/cdrom  disk        CDDVDW SH-224DB
/0/8/0.0.0      /dev/sda    disk        120GB ST120HM000-1G514
/0/9/0.0.0      /dev/sdb    disk        1TB ST1000DX001-1CM1
/0/a/0.0.0      /dev/sdc    disk        MFC-240C
/0/a/0.0.0/0    /dev/sdc    disk

---

### Post by ccct007 on 2014-09-11
Yes I want to know if I have a regular sata hhd or a ssh or a sshd hard drive.

---

### Post by ccct007 on 2014-09-11
The one I'm talking about is the [COLOR=#000000]/0/9/0.0.0 /dev/sdb disk 1TB ST1000DX001-1CM1[/COLOR]

---

### Post by QIII on 2014-09-11
The 120GB drive is a Seagate SSD.

The 1TB drive is a Seagate hybrid.

---

### Post by ccct007 on 2014-09-11
OK thank you. That is what I was supposed to of got.....

---

### Post by ccct007 on 2014-09-11
> **QIII said:**
> The 120GB drive is a Seagate SSD.

The 1TB drive is a Seagate hybrid.

May I ask how you can tell the difference?

---

### Post by Bucky Ball on 2014-09-11
> **ccct007 said:**
> May I ask how you can tell the difference?

Because QIII has magic powers ... and that looks like the model numbers next to the drives. ;)

... but I could be wrong.

Update: no, they're the model numbers. ;)

---

### Post by QIII on 2014-09-11
Oh, man!  You took away the mystery and wonder!

---

