---
title: "where is my /dev/hdg and /dev/sda"
date: 2006-11-28
forum: General Help
---

### Post by yacc45 on 2006-11-28
I have a system running Ubuntu Dapper.  I downgraded the kernel from Linux 2.6.15 to a custom built Linux 2.6.12 kernel. Everything else works fine but the disk devices (/dev/hdg, /dev/sda etc.) are missing. 

When I use 2.6.15 kernel, fdisk -l returns the following:
-------------------------------------------------------------
Disk /dev/hdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1          13      104391   83  Linux
/dev/hdg2              14       10211    81915435   83  Linux
/dev/hdg3           10212       11230     8185117+  82  Linux swap / Solaris
/dev/hdg4           11231       19457    66083377+   f  W95 Ext'd (LBA)
/dev/hdg5           11231       11484     2040223+  83  Linux
/dev/hdg6           11485       19457    64043091   83  Linux

Disk /dev/sda: 73.4 GB, 73407865856 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          15      120456   fc  Unknown
/dev/sda2              16        8924    71561542+  fb  Unknown
-------------------------------------------------------------

But when I use 2.6.12, fdisk -l returns nothing.  Any clue?

---

### Post by ~LoKe on 2006-11-28
When you compiled your kernel, you didn't include support for SATA controllers.

---

### Post by yacc45 on 2006-11-28
I did have SATA configured.  My main disk is an IDE disk.  So at least, /dev/hdg* shouldn't be gone.

---

### Post by yacc45 on 2006-11-28
Here is part of the output from evms_gather_info.  It looks the evms tools can see the hidden partitions. But these partitions were not mapped to any node under /dev. (Neither "/dev/hdg" nor "/dev/evms/hdg" exists). Can anybody figure out something from the output of evms_gather_info?

--------------------------------------------------------
EVMS Command Line Interpreter Version 2.5.4

Logical Disk Name: hdg
Major: 34
Minor: 0
Active: TRUE
Logical Disk Size: 149.05 GB
Logical Disk Geometry: 19457 Cylinders, 255 Heads, 63 Sectors per Track, 512 Bytes per Sector
LBA of the 1024 Cylinder Limit: 16434495

Parents:
  hdg_mbr
  hdg1
  hdg2
  hdg3
  hdg_ebr0
  hdg5
  hdg_ebr1
  hdg6
  hdg_freespace1

Children:

Segment Name: hdg_mbr
Major: 0
Minor: 0
Active: FALSE
Segment Size: 31.50 KB
Starting LBA: 0
Segment Type: Metadata

Parents:

Children:
  hdg


Segment Name: hdg1
Major: 0
Minor: 0
Active: FALSE
Segment Size: 101.94 MB
Starting LBA: 63
Segment Type: Data

This segment may be shrunk using the Shrink command.
The following options are available for shrinking this segment:
Option Name: Size
Description: Use this option to specify how much space to remove from the segment. Remember that segments shrink by cylinder size amounts.
Option Type: A 64 bit positive integer number.

Parents:
  /dev/evms/hdg1

Children:
  hdg


Segment Name: hdg2
Major: 0
Minor: 0
Active: FALSE
Segment Size: 78.12 GB
Starting LBA: 208845
Segment Type: Data

This segment may be shrunk using the Shrink command.
The following options are available for shrinking this segment:
Option Name: Size
Description: Use this option to specify how much space to remove from the segment. Remember that segments shrink by cylinder size amounts.
Option Type: A 64 bit positive integer number.

Parents:
  /dev/evms/hdg2

Children:
  hdg

Segment Name: hdg3
Major: 0
Minor: 0
Active: FALSE
Segment Size: 7.81 GB
Starting LBA: 164039715
Segment Type: Data

This segment may be shrunk using the Shrink command.
The following options are available for shrinking this segment:
Option Name: Size
Description: Use this option to specify how much space to remove from the segment. Remember that segments shrink by cylinder size amounts.
Option Type: A 64 bit positive integer number.

Parents:
  /dev/evms/hdg3

Children:
  hdg


Segment Name: hdg_ebr0
Major: 0
Minor: 0
Active: FALSE
Segment Size: 31.50 KB
Starting LBA: 180409950
Segment Type: Metadata

Parents:

Children:
  hdg

Segment Name: hdg5
Major: 0
Minor: 0
Active: FALSE
Segment Size: 1.95 GB
Starting LBA: 180410013
Segment Type: Data

This segment may be shrunk using the Shrink command.
The following options are available for shrinking this segment:
Option Name: Size
Description: Use this option to specify how much space to remove from the segment. Remember that segments shrink by cylinder size amounts.
Option Type: A 64 bit positive integer number.

Parents:
  /dev/evms/hdg5

Children:
  hdg


Segment Name: hdg_ebr1
Major: 0
Minor: 0
Active: FALSE
Segment Size: 31.50 KB
Starting LBA: 184490460
Segment Type: Metadata

Parents:

Children:
  hdg

Segment Name: hdg6
Major: 0
Minor: 0
Active: FALSE
Segment Size: 61.08 GB
Starting LBA: 184490523
Segment Type: Data

Parents:
  /dev/evms/hdg6

Children:
  hdg


Segment Name: hdg_freespace1
Major: 0
Minor: 0
Active: FALSE
Segment Size: 2.49 MB
Starting LBA: 312576705
Segment Type: Freespace

This segment may be used with the Allocate command, as well as the Create command, to create a segment.

Parents:

Children:
  hdg


Volume Name: /dev/evms/hdg1
Major: 0
Minor: 0
Active: FALSE
Volume Size: 101.94 MB
Minor Number: 0
This volume is not mounted.
The volume is either unformatted or contains a filesystem for which EVMS does not currently have an FSIM.

The following commands may be used with this volume:
     Delete
     Format
     Revert

Children:
  hdg1



Volume Name: /dev/evms/hdg2
Major: 0
Minor: 0
Active: FALSE
Volume Size: 78.12 GB
Minor Number: 0
This volume is not mounted.
The volume is either unformatted or contains a filesystem for which EVMS does not currently have an FSIM.

The following commands may be used with this volume:
     Delete
     Format
     Revert

Children:
  hdg2


Volume Name: /dev/evms/hdg3
Major: 0
Minor: 0
Active: FALSE
Volume Size: 7.81 GB
Minor Number: 0
This volume is not mounted.
The volume is either unformatted or contains a filesystem for which EVMS does not currently have an FSIM.

The following commands may be used with this volume:
     Delete
     Format
     Revert

Children:
  hdg3

Volume Name: /dev/evms/hdg5
Major: 0
Minor: 0
Active: FALSE
Volume Size: 1.95 GB
Minor Number: 0
This volume is not mounted.
The volume is either unformatted or contains a filesystem for which EVMS does not currently have an FSIM.

The following commands may be used with this volume:
     Delete
     Format
     Revert

Children:
  hdg5


Volume Name: /dev/evms/hdg6
Major: 0
Minor: 0
Active: FALSE
Volume Size: 61.08 GB
Minor Number: 0
This volume is not mounted.
The volume is either unformatted or contains a filesystem for which EVMS does not currently have an FSIM.

The following commands may be used with this volume:
     Format

Children:
  hdg6
--------------------------------------------------------

---

