---
title: "How To Recover LVM Data With Missing Disk?"
date: 2012-11-30
forum: General Help
---

### Post by brianafischer on 2012-11-30
I have a stack hard drives from old computers that I have been recovering data from.  I ran into one that contains an LVM Volume.

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63   586067264   293033601   8e  Linux LVM
```

I believe this was one of many disks I used in a LVM volume a few years ago.  I am not sure where the other drives in the LVM volume are located.  How can I recover data from this disk?

---

### Post by dcstar on 2012-12-01
> **brianafischer said:**
> I have a stack hard drives from old computers that I have been recovering data from.  I ran into one that contains an LVM Volume.

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63   586067264   293033601   8e  Linux LVM
```

I believe this was one of many disks I used in a LVM volume a few years ago.  I am not sure where the other drives in the LVM volume are located.  How can I recover data from this disk?

Without knowing **exactly** what the original configuration of the RAID array was, then you probably cannot.

The disk could have been part of a RAID-0, 1, 5 or whatever and without that information and the other disks in the array then the odds of recovering anything are low.

---

