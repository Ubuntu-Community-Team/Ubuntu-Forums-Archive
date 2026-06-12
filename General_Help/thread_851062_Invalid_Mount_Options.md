---
title: "Invalid Mount Options"
date: 2008-07-06
forum: General Help
---

### Post by Throbkin on 2008-07-06
I've been tinkering with trying to get my Sansa250 MP3 player mounted. It originally just had some difficulties mounting read/write consistently. So I messed with the mount options through Gnome and now I get 'invalid mount options' everytime I plug in the USB. I've tried different USB slots, but fdisk still gets this:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1        1002     1985539+   6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 16, 10) logical=(0, 16, 26)
Partition 1 has different physical/logical endings:
     phys=(247, 64, 9) logical=(1001, 2, 4)
Partition 1 does not end on cylinder boundary.
```

And fstab still doesn't recognize it, which I think is correct, right? Because it's an external device? 

So my question is, how do I remount this device with read-write options only? My attempts thus far with mount have all said that it can't find the device in fstab or mtab. Now what?

---

### Post by Eric101 on 2008-07-06
Do you have the USB mode on the Sansa set to MSC?

---

### Post by Throbkin on 2008-07-06
> **Eric101 said:**
> Do you have the USB mode on the Sansa set to MSC?

I do.

---

