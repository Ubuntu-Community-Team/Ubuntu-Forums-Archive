---
title: "Hardware RAID array, partitioning issue"
date: 2014-05-04
forum: General Help
---

### Post by spockswhitepants on 2014-05-04
I am transitioning a server from Windows to Linux. On this server I have a hardware RAID 6 array being ran off a real PCIe server RAID controller. It shows up as one big disk under the OS. Under Windows I was able to use Drive Administration to shrink the existing NTFS partition. But when I go to create a new ext4 partition in the space, everything in KDE Partition Manager that I can normally do with the partitions is disabled (just for that array). Why is that? Do I need to use a different tool to create a partition on this drive?

EDIT: I figured out the issue I think... looks like it is a size limitation with fdisk (which I assume is what KDE Partition Manager is using behind the scenes). The existing partition and free space were over 2GB in size so it was just disabling all the options. I was able to partition it using parted from the console.

---

