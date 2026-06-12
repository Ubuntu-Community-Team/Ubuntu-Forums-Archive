---
title: "/media/&lt;LABEL&gt; or &lt;UUID&gt; Quick Questions."
date: 2014-12-16
forum: General Help
---

### Post by mikodo on 2014-12-16
These are for an external drive's partition. (For backup, as an example).

```
/media/<**UUID>**/backup/whatever 
or 
media/<**LABEL>**/backup/whatever
```
Are these equally fine to use?

Is  that how to write the path for a LABEL? I have used the UUID's, but never used a label before.  


Reading from here: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

*"By default, external drives automatically mounted at /media/disk then /media/disk-1  and so on.  This is not very helpful when trying to find the drive you  are looking for, especially if you have multiple devices plugged in.   Labeled devices that are automatically mounted will be mounted in the /media directory using their label as the mount point, /media/<label>.  ex: /media/my_external" *

Reading from here:  [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

*"Linux now prefers to use **UUID** (Universally Unique Identifier), **LABEL**, or symlinks to identify media storage devices on a system.  Directly using /dev/hd*# or /dev/sd*# is no longer preferred since these device assignments can change between system boots: all filesystems should be specified by UUID=<id> or LABEL=<name> for each partition."*

---

### Post by oldfred on 2014-12-16
External devices are auto mounted. If the partition has a label then it will mount with the label, otherwise it uses the UUID. You do not have to manually mount, but can.

And you can use gparted to create labels when partitioning, with right click. Or you can use Disks but often have to unmount partition to assign a label.

I labelled mine, label means something to me as it was from MicroCenter and is 4GB flash drive.
```

device     fs_type label        mount point            UUID
/dev/sdc1  vfat    MC4GB    /media/fred/MC4GB     E489-24AF

```

---

### Post by mikodo on 2014-12-16
> **oldfred said:**
> External devices are auto mounted. If the partition has a label then it will mount with the label, otherwise it uses the UUID. You do not have to manually mount, but can.

And you can use gparted to create labels when partitioning, with right click. Or you can use Disks but often have to unmount partition to assign a label.

I labelled mine, label means something to me as it was from MicroCenter and is 4GB flash drive.
```

device     fs_type label        mount point            UUID
/dev/sdc1  vfat    MC4GB    /media/fred/MC4GB     E489-24AF

```Thanks Fred. It was in another response to me, that you mentioned using labels. That is why I started looking into them.  :p

Kind Regards.

---

