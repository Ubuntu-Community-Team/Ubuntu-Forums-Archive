---
title: "I can't open one partition"
date: 2008-05-01
forum: General Help
---

### Post by _Jorge_ on 2008-05-01
Hi, Im newbie with Ubuntu (Hardy Heron).

Since I installed ubuntu I can access to windows partition, but not to another partition of the same hard disk (in which there are only photos) and in Windows I can access perfectly to this partition.

I receive this text when I try to open this partition:

```
    mount: wrong fs type, bad option, bad superblock on /

    dev/sda5,      missing codepage or helper program,

    or other error        In some cases useful info is found

    in syslog -try         dmesg | tail or so
```

 

And when I wrote in to the terminal dmesg | tail:

```
    [   50.564906] eth0: no IPv6 routers present
    [   52.701806] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
    [   52.702703] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
    [   52.703480] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
    [  529.354985] EXT3-fs warning: feature flags set on rev 0 fs, running e2fsck is recommended
    [  529.363808] EXT3-fs: journal inode is deleted.
    [ 1341.870277] EXT3-fs warning: feature flags set on rev 0 fs, running e2fsck is recommended
    [ 1341.870988] EXT3-fs: journal inode is deleted.
    [ 1820.670773] EXT3-fs warning: feature flags set on rev 0 fs, running e2fsck is recommended
    [ 1820.671751] EXT3-fs: journal inode is deleted.
```

 
My fstab information:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda6 :
UUID=9ba73414-e044-4d80-9aec-230f1c68bfcf	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=6E6446186445E405	/media/disk	ntfs-3g	defaults,nosuid,nodev,uhelper=hal,locale=es_ES.UTF-8	0	0
#Entry for /dev/sda7 :
UUID=25e12181-fffc-465e-b282-20b0eac37555	none	swap	sw	0	0
/dev/scd1	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/scd0	/media/cdrom1	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0

```

I know, I've given a lot of information, but I hope you can help me!

PS: Sorry for my bad english!

---

### Post by danwood76 on 2008-05-01
COuld you post an fdisk list aswell please?

```

sudo fdisk -l

```

---

### Post by _Jorge_ on 2008-05-02
Here is the fdisk

```
Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x43544353

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       11655    93618756    7  HPFS/NTFS
/dev/sda2           11674       14593    23454900    f  W95 Ext'd (LBA)
/dev/sda3           11656       11673      144585   83  Linux
/dev/sda5           12809       14593    14337981    7  HPFS/NTFS
/dev/sda6           11674       12753     8675037   83  Linux
/dev/sda7           12754       12808      441756   82  Linux swap / Solaris
```

---

### Post by danwood76 on 2008-05-02
if you open your fstab for writing:
```

sudo gedit /etc/fstab

```
add this line to the bottom:
```

/dev/sda5    /media/disk2    ntfs-3g	defaults,nosuid,nodev,uhelper=hal,locale=es_ES.UTF-8	0	0

```
Save the file, then create the new mountpoint.
```

sudo mkdir /media/disk2

```
You can replace disk2 in the above lines with whatever you want the disk to come up with.

For example if I wanted to call it photos the fstab line would be:
```

/dev/sda5    /media/photos    ntfs-3g	defaults,nosuid,nodev,uhelper=hal,locale=es_ES.UTF-8	0	0

```
and the command to make the mountpoint would be:
```

sudo mkdir /media/photos

```

---

### Post by _Jorge_ on 2008-05-02
yeah! it works! thanks for all danwood76 ;)

---

