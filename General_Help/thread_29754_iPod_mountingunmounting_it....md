---
title: "iPod mounting/unmounting it..."
date: 2005-04-25
forum: General Help
---

### Post by cusco on 2005-04-25
Sory... I didn't knew where to post this...

ok I have gtkpod which was working just fine and then I screwd up... I disconected my ipod from the cable has I was in a hurry

now when I conect it:

cusco@Portatil:~$ dmesg | tail
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
SCSI device sda: 7999488 512-byte hdwr sectors (4096 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: [mac] p1 p2 p3
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete
**HFS+-fs warning: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.**

so I should run fsck....

cusco@Portatil:~$ fsck /dev/sda3
fsck 1.35 (28-Feb-2004)
**fsck: fsck.hfs: not found**
fsck: Error 2 while executing fsck.hfs for /dev/sda3

ok so I downloaded hfsplus from apt

then I have this error:

cusco@Portatil:~$ sudo hpfsck -v /dev/sda3
*** Checking Volume Header:
Volume is wrapped in HFS volume  (use hfsck to check this)
Embedded HFS+ volume at 0x53000 (0x790D00) of 0x200 sized Blocks
signature       : +H
version         : 4
attributes      : 0X2800
last_mount_vers : 0.01
reserved        : 32
create_date     : Thu Jan 15 18:44:49 2004
modify_date     : Mon Apr 25 18:21:35 2005
backup_date     : Thu Dec 31 23:23:28 1903
checked_date    : Fri Jan 16 02:44:49 2004
file_count      : 184
folder_count    : 60
blocksize       : 1000
total_blocks    : 991648
free_blocks     : 759168
next_alloc      : 233493
rsrc_clump_sz   : 65536
data_clump_sz   : 65536
next_cnid       : 559
write_count     : 1335
encodings_bmp   : 0X1
                  Allocation file
total_size          : 0X1F000
clump_size          : 0X1F000
total_blocks        : 0X1F
extents             : (0X1+0X1F) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0)
                  Extension file
total_size          : 0X400000
clump_size          : 0X400000
total_blocks        : 0X400
extents             : (0X821+0X400) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0)
                  Catalog file
total_size          : 0X600000
clump_size          : 0X600000
total_blocks        : 0X600
extents             : (0XC21+0X600) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0)
                  Attribute file
total_size          : 0
clump_size          : 0
total_blocks        : 0
extents             : (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0)
                  Start file
total_size          : 0
clump_size          : 0
total_blocks        : 0
extents             : (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0)
Volume was not cleanly unmounted
Volume is inconsistent
Reserved attribute in use: 2000
Volume was last Mounted by unknnown implemenatation:
0.01                                            Done ***
*** Checking Backup Volume Header:
signature       : +H
version         : 4
attributes      : 0X2900
last_mount_vers : JSFH
reserved        : 32
create_date     : Thu Jan 15 18:44:49 2004
modify_date     : Mon Apr 25 13:25:09 2005
backup_date     : Thu Dec 31 23:23:28 1903
checked_date    : Fri Jan 16 02:44:49 2004
file_count      : 183
folder_count    : 60
blocksize       : 1000
total_blocks    : 991648
free_blocks     : 759164
next_alloc      : 233491
rsrc_clump_sz   : 65536
data_clump_sz   : 65536
next_cnid       : 555
write_count     : 1334
encodings_bmp   : 0X1
                  Allocation file
total_size          : 0X1F000
clump_size          : 0X1F000
total_blocks        : 0X1F
extents             : (0X1+0X1F) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0)
                  Extension file
total_size          : 0X400000
clump_size          : 0X400000
total_blocks        : 0X400
extents             : (0X821+0X400) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0)
                  Catalog file
total_size          : 0X600000
clump_size          : 0X600000
total_blocks        : 0X600
extents             : (0XC21+0X600) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0)
                  Attribute file
total_size          : 0
clump_size          : 0
total_blocks        : 0
extents             : (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0)
                  Start file
total_size          : 0
clump_size          : 0
total_blocks        : 0
extents             : (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0) (0+0)
Volume is inconsistent
Reserved attribute in use: 2000
Volume was last Mounted by unknnown implemenatation:
JSFH                                            Done ***
*** Checking Extents Btree:
  depth       : 0
  root        : 0
  leaf_count  : 0
  leaf_head   : 0
  leaf_tail   : 0
  node_size   : 0X1000
  max_key_len : 0XA
  node_count  : 0X400
  free_nodes  : 0X3FF
  reserved1   : 0
  clump_size  : 0X400000
  btree_type  : 0
  reserved2   : 0
 !HFSPLUS_BAD_CLOSE HFSPLUS_TREE_BIGKEYS  !HFSPLUS_TREE_VAR_NDXKEY_SIZE
Node descriptor for Node 0
next     : 0
prev     : 0
height   : 0
num_rec  : 0
reserved : 0
height   : 0
HFSP_NODE_NDX
                                                Done ***
*** Checking Catalog Btree:
  depth       : 0X2
  root        : 0X3
  leaf_count  : 0X1EA
  leaf_head   : 0X2
  leaf_tail   : 0X8
  node_size   : 0X2000
  max_key_len : 0X204
  node_count  : 0X300
  free_nodes  : 0X2F4
  reserved1   : 0
  clump_size  : 0X600000
  btree_type  : 0
  reserved2   : 0XCF
 !HFSPLUS_BAD_CLOSE HFSPLUS_TREE_BIGKEYS  HFSPLUS_TREE_VAR_NDXKEY_SIZE
Node descriptor for Node 3
next     : 0
prev     : 0
height   : 0X2
num_rec  : 10
reserved : 0
height   : 0X2
HFSP_NODE_NDX
Node    3, Record  0 is at pos 0E00,Backptr is at offset 1FFE
Node 3 with 10 records is damaged trying to fix ***
Node    3, Record  0 is at pos 0E00,Backptr is at offset 1FFE
checkbtree_key_by_index: offset out of range 2200 >= 2000
                                *** Check stopped ***
hpfsck: hpfsck: Invalid key length in record_readkey (Invalid argument)
cusco@Portatil:~$



in the end what happens is that iPod is mounted but its nott writtable! Please .. any ideias? 

thanks

---

### Post by dude2425 on 2005-05-07
I just got myself an iPod, and got the same problem. What you wan't to do is convert the filesystem to FAT32 instead of hfs+ because Linux doesn't have any tools to work with hfs+ very well yet. I can now write anywhere on my brand new iPod.

---

