---
title: "partition permission ???"
date: 2007-04-19
forum: General Help
---

### Post by naseem on 2007-04-19
Hi i'm tring to create a virtual box directory to mount a new guest os in a disk but seams that I don't have the right permission
I just reformattede in ext3 the sda1 partition
and added to etc/fstab this line:
# /dev/sda1
/dev/sda1 /media/sda1   ext3   defaults   0   2

but now I cannot access "ex crate a folder" in sda1 as normal user, and the same permission error is given by virtualbox when I try tr create the filesistem in thet partition

this is output from ls -la /dev
```
brw-rw----  1 root disk        8,   0 2007-04-19 13:27 sda
brw-rw----  1 root disk        8,   1 2007-04-19 13:28 sda1
brw-rw----  1 root disk        8,  16 2007-04-19 15:25 sdb
brw-rw----  1 root disk        8,  17 2007-04-19 15:25 sdb1
brw-rw----  1 root disk        8,  18 2007-04-19 13:25 sdb2
brw-rw----  1 root disk        8,  19 2007-04-19 15:25 sdb3
brw-rw----  1 root disk        8,  21 2007-04-19 13:25 sdb5
brw-rw----  1 root disk        8,  22 2007-04-19 13:25 sdb6
brw-rw----  1 root disk        8,  23 2007-04-19 13:25 sdb7
brw-rw----  1 root disk        8,  32 2007-04-19 15:25 sdc
brw-rw----  1 root disk        8,  33 2007-04-19 13:25 sdc1
brw-rw----  1 root disk        8,  37 2007-04-19 13:28 sdc5
brw-rw----  1 root disk        8,  38 2007-04-19 13:25 sdc6
brw-rw----  1 root disk        8,  39 2007-04-19 13:25 sdc7

```

but for instance sdb2 is perfectly acessible and i can write and read...so I'm puzled:( 

please help!

---

### Post by fanatik on 2007-04-19
can you give the output of:

$ mount | grep sda1

Thanks,

---

### Post by naseem on 2007-04-19
this is what I get:
/dev/sda1 on /media/sda1 type ext3 (rw)

but when I try to create folder image in virtualbox this is what I get:
Falied to create a hard disk image '/media/sda1/vista.vdi' (VERR_ACCESS_DENIED).


Result Code: 
0x80004005
Component: 
VirtualDiskImage
Interface: 
IVirtualDiskImage {a8265b5a-0d20-4a46-a02f-65693a4e8239}

---

### Post by kellemes on 2007-04-19
Are you a member of group vboxusers?

By the way.. are you trying to get a guest os on virtual partition? Or do you want to mount an existing guest os?

---

### Post by naseem on 2007-04-19
trying to get a guest os on virtual
but seams it solved eraising the partition and then using gparted in feisty to ctreate it again
now seams it's working
 thanks!

---

