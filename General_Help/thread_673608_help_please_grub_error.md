---
title: "help please grub error"
date: 2008-01-20
forum: General Help
---

### Post by bizarrechaos on 2008-01-20
im dual booting xp and gutsy
all of a sudden i startup get 
grub loading stage 1.5

grub loading, please wait....
error 2
im on a live cd now
my sudo fdisk -l


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b947b94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4       32098+  de  Dell Utility
/dev/sdb2   *           5       19028   152810280    7  HPFS/NTFS
/dev/sdb3           19029       19452     3405780   db  CP/M / CTOS / ...

Disk /dev/sdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b276b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4776    38363188+  83  Linux
/dev/sdc2            4777        4982     1654695    5  Extended
/dev/sdc5            4777        4982     1654663+  82  Linux swap / Solaris

the linux hd will not mount
i get 
mount:wrong fs type, bad option, bad superblock on /dev/sdc1
the dmesg
[  583.372026] EXT3-fs error (device sdc1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 65569188)!
[  583.379760] EXT3-fs: group descriptors corrupted!
[  598.357072] EXT3-fs error (device sdc1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 65569188)!
[  598.361936] EXT3-fs: group descriptors corrupted!
[ 1960.472236] EXT3-fs error (device sdc1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 65569188)!
[ 1960.478973] EXT3-fs: group descriptors corrupted!
[ 1997.494923] EXT3-fs error (device sdc1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 65569188)!
[ 1997.502906] EXT3-fs: group descriptors corrupted!
[ 2647.372999] EXT3-fs error (device sdc1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 65569188)!
[ 2647.381231] EXT3-fs: group descriptors corrupted!
can some one please help i need my computer back i have alot of work to do and nothing will but im desperate help greatly appreciated

---

### Post by bizarrechaos on 2008-01-20
bumb please help

---

### Post by torgrot on 2008-01-20
Please post your /boot/grub/menu.lst

torgrot

---

### Post by DjBones on 2008-01-20
well assuming you can't boot into either operating system,
you could copy/paste the file 'menu.lst' which is in your /boot/grub folder onto the forums from the ubuntu livecd
then we'll be able to figure out what changes you need to make..

there are grub rescue cd's out here, but i'm not well read on them

---

### Post by bizarrechaos on 2008-01-20
see i cant acess it cause the linux hd wont mount

---

### Post by bizarrechaos on 2008-01-21
bump anyone

---

### Post by gspat on 2008-01-21
boot from your live-cd and try to mount the partition...

if you can, try running fsck on it (check for errors)

---

### Post by bizarrechaos on 2008-01-21
when i try and mount i get mount:wrong fs type, bad option, bad superblock on /dev/sdc1
is there any way to reformat the drive and install ubuntu again

---

### Post by bizarrechaos on 2008-01-21
i just took it downstairs to a windows pc and re formatted it anf im gonna reinstall gutsy hope that works i have a feeling that it might not fix the grub error does anyone have any advice

---

