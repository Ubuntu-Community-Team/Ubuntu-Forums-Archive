---
title: "mount: wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or he"
date: 2019-09-21
forum: General Help
---

### Post by haled on 2019-09-21
Hi everyone, 
I have a partition running on my Mac with Ubuntu 16.04 LTS. It started recently that I could only boot into a black screen in Mac OS and now the partition in the boot menu has completely disappeared. Since Ubuntu still runs top I would like to use it to access my Mac partition and backup the data. Unfortunately I can't mount it and get the following error message: "mount: wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error" I hope you can help me. 
Also any other idea how I could get the data from the Mac partition is more then welcome. 
Thanks a lot :-)

pd.: to mount the drive I tried the commands:

```
sudo mount -o force /dev/sda2 /media/mntpoint/
```

```
sudo mount -t auto /dev/sda2 /media/mntpoint/
```

---

### Post by Autodave on 2019-09-21
If the superblock is bad, you are not likely to get anything from the drive.  The first thing that you need to do is to clone the drive and then work only on the one or the other.  Get a copy made now before any more data is lost.

---

### Post by Yellow Pasque on 2019-09-21
You do have hfsplus and hfsprogs packages installed, correct?

---

### Post by yancek on 2019-09-21
> You do have hfsplus and hfsprogs packages installed, correct? 				

That would be the first thing to check/do as very few if any LInux systems have that software installed in a default installation.

---

### Post by haled on 2019-09-22
Thanks for that advice!! 
Would you clone the entire drive or just the mac partition? Cloning with dd command sounds good?

---

### Post by haled on 2019-09-22
Thanks for the answers :-) 
hfsplus and hfsprogs both are installed.

---

