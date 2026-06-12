---
title: "Since last kernel update no lowercase labels for usb devices"
date: 2015-11-07
forum: General Help
---

### Post by lou6 on 2015-11-07
I tried to rename a usb drive in Gparted today to "backup" but Gparted changes it to "BACKUP".

Earlier today an rsync backup that I run regularly did a complete backup instead of incremental to a usb device labeled "backup".

I did some research RE: changing label names in Gparted and one answer mentioned a parameter in the kernel as being involved in the use of upper/lower case.

Is anyone else experiencing anything odd along these lines? This just started after upgrade to 3.13.0-67.

EDIT: after more checking I discovered that the upper/lower naming issue only apples to fat32 naming. I was able to format a usb stick to ntfs and give it a lowercase label. 

In the past I have always used fat32 sticks for backup of personal data to ensure compatibility with other devices/systems.

FURTHER EDIT: found this to be due to a change to GParted - they say it's not a bug (but it is if you use usb sticks formatted as fat32 with lowercase characters in the filename).

I'm marking this as solved...

---

