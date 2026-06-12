---
title: "Recover ubuntun in boot.ini"
date: 2008-06-15
forum: General Help
---

### Post by albries on 2008-06-15
Hi, First, im sorry if my english is bad, but i dont speak it very well.
I dont know exactly why (maybe because windows sucks) but i have a problem with the boot and i had  to restart the boot to load again my partitions, i recover the windows xp partition in the boot list but i dont know how can i add my Ubuntu partition to the boot.ini file or whatever I have to do.

Currently in my boot.ini i have this:
```

[boot loader]
timeout=20
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Virous XP" /fastdetect

```

one thing i test is add this line(in a forum i read something like this, but it didnt work):
```
D:\wubildr="Ubuntu Hardy Heron"
```

Have a great day!:)

---

### Post by ago on 2008-06-16
It must be C: even if it is installed on D

C:\wubildr.mbr="Ubuntu Hardy Heron"

Make sure that the ?:\ubuntu\winboot\wubildr* are copied to the root of the boot drive

---

### Post by mhousel on 2008-06-21
> **ago said:**
> It must be C: even if it is installed on D

C:\wubildr.mbr="Ubuntu Hardy Heron"

Make sure that the ?:\ubuntu\winboot\wubildr* are copied to the root of the boot driveFirst part works and now I can select Ubuntu, but of course it fails to boot.

Where do we get this if we cannot see the partition that Ubuntu is installed on from Windows?

---

