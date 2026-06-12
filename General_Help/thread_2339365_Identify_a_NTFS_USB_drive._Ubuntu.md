---
title: "Identify a NTFS USB drive. Ubuntu"
date: 2016-10-07
forum: General Help
---

### Post by mikeincousa on 2016-10-07
I have been looking for a way to identify a USB drive installed after boot. 

Hot-pluged? Not sure on the term.


It does *not* show in response to the utilities like blkid

So it seemed to me that this would the most definitive approach:

cd to /dev/disk/.. then head for the sub-directories.

But I am not finding it there, i tried by-label.

That sub-directory shows a FAT drive with its label, so the idea works.

But I am missing something for getting the same info for a NTFS.


It looks like Ubuntu sees the drive. 

After I plug it in the green light on the drive flashes a couple of time, then settles to steady-state on.

[COLOR=#000000][FONT=Georgia]The drive label shows nicely in Windows 10.

Any help and direction will be appreciated.
[/FONT][/COLOR]

---

### Post by DuckHook on 2016-10-07
For the 'buntus, the convention for USB drives tend to be:```
/dev/sr#
```…where # is a number starting from 0. Examples: sr0, sr1, sr2, etc. I'm not sure about:```
/dev/disk/???
```…because disks might not show there unless mounted first.

Are you running DEs? Not a server flavour? Is it Ubuntu? Xenial? If so, then the udev system should automatically detect any added drive and automount it. This is what is meant by hot-plugged.

Also, *blkid* must be run with *sudo*.

In fact, with the drive plugged in, please post the output of:```
sudo blkid
``````
sudo parted -l
``````
lsusb
```

---

