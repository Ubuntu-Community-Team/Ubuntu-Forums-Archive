---
title: "Best software to restore a Ext4 thumbdrive?"
date: 2017-04-02
forum: General Help
---

### Post by Arminius on 2017-04-02
I have a thumbdrive I use on my Rasberri Pi, but everynow and then the thing freezes, and half the time the thumb drive refuses to mount, usually I just format and start over, but I'm getting tired of losing my data, what's the best diagnosticand recovery software for such things?

---

### Post by Arminius on 2017-04-02
For anyone who comes after the answer is GParted Partition Editor

---

### Post by sudodus on 2017-04-02
You can repair the file system when plugged into a computer running linux.

If connected via USB,

```
sudo e2fsck -f /dev/sdxn
```

where **x** is the drive letter and **n** the partition number.

Otherwise

```
sudo e2fsck -f /dev/mmcblkmpn
```

where **m** is the card number and **n** the partition number, for example /dev/mmcblk0p1

You find the device specification via these commands

```
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
```

See this link for more details, [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

