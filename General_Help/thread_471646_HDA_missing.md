---
title: "HDA missing"
date: 2007-06-12
forum: General Help
---

### Post by vapore0n on 2007-06-12
I had Windows Xp installed on the first partition of the drive, hda drive. I was using vmplayer to run that existing installation of XP in Ubuntu. Worked pretty good. Till yesterday. 

> VMware Player cannot find the virtual disk "/home/zip-it/My Documents/VMWare/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/home/zip-it/My Documents/VMWare/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.

I have not changed the vmdk files. Here they are:
```

# Disk DescriptorFile
version=1
CID=f31761bc
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "windowsxp.mbr" 0
RW 78140096 FLAT "/dev/hda" 63 

# The Disk Data Base 
#DDB

ddb.toolsVersion = "6530"
ddb.adapterType = "ide"
ddb.virtualHWVersion = "4"
ddb.geometry.sectors = "63"
ddb.geometry.heads = "255"
ddb.geometry.cylinders = "4864"

```

I cant find /dev/hda anymore. I think it was there.
I tried following the procedures again to reuse that partition, and while using parted I get this now:
> Error: Could not stat device hda - No such file or directory. 

I can still run XP if I choose it from the boot menu (albeit safe mode).

Any help?

---

### Post by vapore0n on 2007-06-12
nevermind

THe system changed from hda to sda. Maybe it was one of those kernel updates?

XP is running good now

---

