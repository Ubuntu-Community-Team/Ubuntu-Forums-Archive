---
title: "Do I mark the disk for crypto first or lvm first"
date: 2014-10-06
forum: General Help
---

### Post by MechaMechanism on 2014-10-06
Do I mark a raw unpartitioned disk for crypto first or do I mark it for lvm and the crypto.

Also how do I combine multiple disk into 1 crypto disk so I only need 1 password for all disk.  I also want the 1 password to unlock the swap.  Using lvm as well.  Basically an encrypted lvm setup combining 4 hard drives.

Do I need to put swap on its own logical volume, probably.

---

### Post by MechaMechanism on 2014-10-07
Figured it out.

What we want to do is combine multiple physical hard drives into one single virtual hard drive.  In this case we will combine 4 physical hard drives into one virtual hard drive.

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```
Repeat for each drive, in my case sdb, sdc, sdd

```
sudo pvcreate /dev/sda
```
Repeat for each drive.

```
sudo vgcreate sol /dev/sda /dev/sdb /dev/sdc /dev/sdd
```
Replace the drive letters with your own.

```
sudo lvcreate -l 100%FREE -n earth sol
```

You can now mark the logical volume earth for use as encryption.  You can do that with the disk program or with the installer.  Then you may format as usual.

```
man pvcreate
```
```
man vgcreate
```
```
man lvcreate
```

[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[http://manpages.ubuntu.com/manpages/precise/man8/lvm.8.html](http://manpages.ubuntu.com/manpages/precise/man8/lvm.8.html)

---

### Post by MechaMechanism on 2014-10-11
Don't create a separate logical volum for swap, if you do it will be very painful to know that you probably can't grow it in size.  Just create one logical volume for root and then create a swap file which is way more flexible and allows you more control over the swap space.  Also this way swap is still encrypted.

---

