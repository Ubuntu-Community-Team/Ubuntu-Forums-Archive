---
title: "vfat disk broken? screwed? i dunno"
date: 2007-11-10
forum: General Help
---

### Post by neoroses on 2007-11-10
rite heyup guys.....a while ago i installed a boot loader on my flash disk usb drive, i am now done with that so i want to format it, but i cannot, it  mounts fine to /dev/sbd1 and /media/usbdisk 1 but when ever i try and delete something of it i get:

Error "I/O error" while deleting "/media/usbdisk 1/what ever the file is". 

gparted wont work, when its unmounted gparted doesnt pick it up atall and when i try and change the permissions of the drive it just doesnt work!!! any ideas???

---

### Post by mlind on 2007-11-10
Try doing
```

sudo umount /dev/sbd1
sudo fsck.vfat -f /dev/sbd1

```

Then reconnect the drive

---

### Post by neoroses on 2007-11-10
ok that didnt work. but i got this:
(the files are the grub files i think)

```
howie@howie-desktop:~$ sudo fsck.vfat -f /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /dev/sdb1:No such file or directory
howie@howie-desktop:~$ sudo fsck.vfat -f /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/x
 Start does point to root directory. Deleting dir. 
/install
 Start does point to root directory. Deleting dir. 
/isolinux
 Start does point to root directory. Deleting dir. 
/pics
 Start does point to root directory. Deleting dir. 
/.Trash-howie/massive attack
 Start does point to root directory. Deleting dir. 
Orphaned long file name part "isolinux"
1: Delete.
2: Leave it.
?  
delete
Invalid input.
? 1
/.Trash-howie/ubuntu-7.04-alternate-i386.iso_FILES/pics/..
  Start (0) does not point to .. (3)
Long filename fragment ":1zh:8xW:DHK:Egb:FA7:3O2:8N-:0qw:3iK:Fo-:D7u:AeJ:2TQ" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
1: Delete fragment
2: Leave it as it is.
3: Set start bit
? 3
Reserved field in VFAT long filename slot is not 0 (but 0x11).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0xe1b4).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ":1zh:8xW:DHK:Egb:FA7:3O2:8N-:0qw:3iK:Fo-:D7u:AeJ:2TQ".
  (Start may have been overwritten by &#65533;&#65533;&#65533;OC &#65533;&#65533;.&#65533;M&#65533;)
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name &#65533;&#65533;&#65533;OC &#65533;&#65533;.&#65533;M&#65533;)
? 3
Wrong checksum for long file name ":1zh:8xW:DHK:Egb:FA7:3O2:8N-:0qw:3iK:Fo-:D7u:AeJ:2TQ".
  (Short name &#65533;&#65533;&#65533;OC &#65533;&#65533;.&#65533;M&#65533; may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name &#65533;&#65533;&#65533;OC &#65533;&#65533;.&#65533;M&#65533;)
? 3     
Reserved field in VFAT long filename slot is not 0 (but 0x67).
1: Fix.
2: Leave it.
? 1
Start cluster field in VFAT long filename slot is not 0 (but 0xe05f).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ":0qj:08X:Eu+:D+4:3fk:7JI:2AY:0VL:54w:8C5:3Xp:0hd:27N".
  (Start may have been overwritten by \024&#65533;&#65533;\202\010&#31722;.2
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name \024&#65533;&#65533;\202\010&#31722;.2
? 3
Wrong checksum for long file name ":0qj:08X:Eu+:D+4:3fk:7JI:2AY:0VL:54w:8C5:3Xp:0hd:27N".
  (Short name \024&#65533;&#65533;\202\010&#31722;.2&#65533;&#65533; may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name \024&#65533;&#65533;\202\010&#31722;.2
? 3
Long filename fragment ":3s8:FIl:5ol:9VQ:Chv:5H6:7q9:8jT:DQw:11o:2vG:3-T:2jj" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
1: Delete fragment
2: Leave it as it is.
3: Set start bit
? 3
Reserved field in VFAT long filename slot is not 0 (but 0xb9).
1: Fix.
2: Leave it.
? 1 
Start cluster field in VFAT long filename slot is not 0 (but 0x754e).
1: Fix.
2: Leave it.
? 1
Unfinished long file name ":3s8:FIl:5ol:9VQ:Chv:5H6:7q9:8jT:DQw:11o:2vG:3-T:2jj".
  (Start may have been overwritten by &#65533;\003O\&#65533;Yh\024.s&#65533;V)
1: Delete LFN
2: Leave it as it is.
3: Fix numbering (truncates long name and attaches it to short name &#65533;\003O\&#65533;Yh\024.s&#65533;V)
? 3
Wrong checksum for long file name ":3s8:FIl:5ol:9VQ:Chv:5H6:7q9:8jT:DQw:11o:2vG:3-T:2jj".
  (Short name &#65533;\003O\&#65533;Yh\024.s&#65533;V may have changed without updating the long name)
1: Delete LFN
2: Leave it as it is.
3: Fix checksum (attaches to short name &#65533;\003O\&#65533;Yh\024.s&#65533;V)
? 3
/.Trash-howie/ubuntu-7.04-alternate-i386.iso_FILES/.disk
  Has a large number of bad entries. (478/508)
Drop directory ? (y/n) y
Root directory is full.
```

---

### Post by mlind on 2007-11-10
can't you just use fdisk and mkfs to re-partition the disk? I'm not sure if this erases the MBR area where grub bootloader is. You can used dd or windows fdisk to remove MBR though.
make sure that the /deb/sdb points to the correct device before doing this or you may remove your linux partition instead.


For some reason I assumed that the filesystem was FAT32, is this correct?

---

### Post by neoroses on 2007-11-10
fixed it with fdisk thanks dude...i did try it before....musta done summit rong tho =)

cheerse

---

