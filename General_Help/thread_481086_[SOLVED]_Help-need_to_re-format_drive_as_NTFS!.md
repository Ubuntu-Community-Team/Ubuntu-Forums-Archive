---
title: "[SOLVED] Help-need to re-format drive as NTFS!"
date: 2007-06-22
forum: General Help
---

### Post by denny14 on 2007-06-22
we have 2 hard drives, and have formatted them both, so each has one partition only. we installed Ubuntu on the first drive, and tried to install Vista on the second, but it won't let us, because it's not in NTFS format. How can we format the second drive as NTFS (bearing in mind Ubuntu is the only operating system currently installed?)

We tried formatting the second drive using the Vista and XP install discs, but both times it said something about it wasn't a valid windows hard drive (probably because it isn't in NTFS format.)

We need help please!
Thanks :)

we deleted the partition on the second drive (using the Vista and XP install discs), and then created a new partition, but it wouldn't let us install the Windows OS on it, in both cases.

---

### Post by wormser on 2007-06-22
Use gparted.  I am pretty sure there is an option to format as NTFS.  Make sure unmount the drive first.

```
sudo gparted
```

---

### Post by ikt on 2008-01-13
> **wormser said:**
> Use gparted.  I am pretty sure there is an option to format as NTFS.  Make sure unmount the drive first.

```
sudo gparted
```

Hi,

I have unmounted the hard drive, and deleted the previous partition, now I am looking to partition it in NTFS, but the NTFS option is greyed out.

Any idea what is going wrong?

The setup is that Ubuntu is on my main drive and I have a second hard drive connected with nothing on it.

----

Fixed it:

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

Needed to install ntfsprogs

---

