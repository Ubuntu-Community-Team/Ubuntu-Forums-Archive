---
title: "Mount usb Drive"
date: 2006-11-12
forum: General Help
---

### Post by dontgetshocked on 2006-11-12
I have a usb hard drive that I would like to use on Ubuntu. When I plug it in  it is not recognized, i.e. seen as a drive. How can I correct this?

---

### Post by jd65pl on 2006-11-12
What is it formatted to?

Could you get gparted partitioning tool and see if it is recognised using that?

```
sudo aptitude update
sudo aptitude install gparted
```

---

### Post by dontgetshocked on 2006-11-12
gparted recognizes it , but does no know what kind of partition it is.
/dev/sda1 unknown     55.88gb
/dev/sda-1 free        7.84mb

---

### Post by jd65pl on 2006-11-12
You have data on the drive then? It may be formatted to ntfs. Could you use a windows machine to find out what it is formatted to?

---

### Post by dontgetshocked on 2006-11-12
it is definitely ntfs for sure

---

### Post by jd65pl on 2006-11-12
See this on how to:

 mount read only - [https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28ntfs%29](https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28ntfs%29)

mount read/write - [https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

---

