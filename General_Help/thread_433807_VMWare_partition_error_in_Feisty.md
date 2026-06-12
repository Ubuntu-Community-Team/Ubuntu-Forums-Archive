---
title: "VMWare partition error in Feisty"
date: 2007-05-05
forum: General Help
---

### Post by joiningtheherd on 2007-05-05
I've just installed VMWare Server on an Ubuntu Feisty / Windows XP SP2 dual boot laptop, because I need to test software, and web-pages in both OS's on a regular basis, and would like to avoid reboots during work. I don't want to waste several GB of drive space with two instances of Windows (one VM and one original). Any idea's why this is happening and what might rectify it?  I tried Qemu, but the darned thing kept wanting me to re-activate windows with every launch of the VM.

The error:
```

Cannot open the disk '/tmp/vm/Windows XP Home Edition/Windows XP Home Edition.vmdk' or one of the snapshot disks it depends on.
Reason: The partition table on the physical disk has changed since the disk was created. Remove the physical disk from the virtual machine, then add it again.

```

This partition table has not been edited for some months now.

The .vmdk for the proposed VM

```

# Disk DescriptorFile
version=1
CID=ab0e0c64
parentCID=ffffffff
createType="partitionedDevice"

# Extent description
RW 63 FLAT "Windows XP Home Edition-pt.vmdk" 0
RW 41945652 FLAT "/dev/sda" 63
RW 2168775 ZERO
RW 63 FLAT "Windows XP Home Edition-pt.vmdk" 63
RW 256977 FLAT "/dev/sda" 44114553
RW 63 FLAT "Windows XP Home Edition-pt.vmdk" 126
RW 6297417 ZERO
RW 63 FLAT "Windows XP Home Edition-pt.vmdk" 189
RW 16466562 ZERO
RW 63 FLAT "Windows XP Home Edition-pt.vmdk" 252
RW 30908997 ZERO
RW 63 FLAT "Windows XP Home Edition-pt.vmdk" 315
RW 94381812 ZERO

# The Disk Data Base
#DDB

ddb.virtualHWVersion = "4"
ddb.geometry.cylinders = "11978"
ddb.geometry.heads = "255"
ddb.geometry.sectors = "63"
ddb.geometry.biosCylinders = "11978"
ddb.geometry.biosHeads = "255"
ddb.geometry.biosSectors = "63"
ddb.adapterType = "buslogic"

```

Output from 'parted':
```

Disk /dev/sda: 192426569s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 63s 41945714s 41945652s primary ntfs boot
2 41945715s 44114489s 2168775s primary ntfs
3 44114490s 192426569s 148312080s extended
5 44114553s 44371529s 256977s logical ext2
6 44371593s 50669009s 6297417s logical linux-swap
7 50669073s 67135634s 16466562s logical reiserfs
9 67135698s 98044694s 30908997s logical reiserfs
8 98044758s 192426569s 94381812s logical reiserfs

(parted) unit cyl
(parted) print

Disk /dev/sda: 11977cyl
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: 11978,255,63. Each cylinder is 8225kB.
Partition Table: msdos

Number Start End Size Type File system Flags
1 0cyl 2610cyl 2610cyl primary ntfs boot
2 2611cyl 2745cyl 135cyl primary ntfs
3 2746cyl 11977cyl 9232cyl extended
5 2746cyl 2761cyl 15cyl logical ext2
6 2762cyl 3153cyl 391cyl logical linux-swap
7 3154cyl 4178cyl 1024cyl logical reiserfs
9 4179cyl 6102cyl 1923cyl logical reiserfs
8 6103cyl 11977cyl 5874cyl logical reiserfs

```

The numbers all seem to add up, and I am sure that nothing has changed as even after several boots back and forth all values are the same as they were when I started this whole affair. I'm flummoxed.

Ideas?

---

