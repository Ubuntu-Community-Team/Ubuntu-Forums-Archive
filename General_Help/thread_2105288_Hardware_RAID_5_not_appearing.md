---
title: "Hardware RAID 5 not appearing"
date: 2013-01-15
forum: General Help
---

### Post by villieb on 2013-01-15
Howdy lovely Ubuntu people!!!

I've gone and installed Ubuntu desktop on a PC that I am planning on using as a file store and media store.

Currently, I have Ubuntu running from a 60Gb SSD and I have 3x2Tb drives which I have configured as a RAID5 array via the motherboard's onboard RAID controller.

Ubuntu see's the RAID controller:

```
00:11.0 RAID bus controller: Advanced Micro Devices [AMD] Hudson SATA Controller [RAID mode] (rev 40)
```But when looking at the drives in GParted, they are appearing as three seperate 2Tb drives...

Can anybody help please?

Thanks

---

### Post by ronparent on 2013-01-17
Install **dmraid** to the system presumably installed on the ssd. That is the program that activates your fakeRAID array to give you access to it.

Someone at this point will probably also tell you to use the linux software raid instead. It doesn't matter. It is more an issue of whether or not you have to access the raid drive with Windows. If not, then you might be better off using the native linux raid with mdadm instead of dmraid.

---

### Post by villieb on 2013-01-17
I ended up going down the soft raid route.

I found a guide which said to format the drives as ext3 which I did... but then others saying ext4.

I started the raid creation last night but then went to bed. Ill check the progress when I get home.

---

