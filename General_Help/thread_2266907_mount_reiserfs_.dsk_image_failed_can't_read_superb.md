---
title: "mount reiserfs .dsk image failed: can't read superblock"
date: 2015-02-26
forum: General Help
---

### Post by jalil2 on 2015-02-26
[COLOR=#000000][FONT=Arial]I have a failed 160 GB Western Digital Netcenter NAS disk and its image after failing in .DSK format.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]When I connect the disk to my ubuntu machine and typed:[/FONT][/COLOR]
```
# losetup -o 512006144 /dev/loop1 /dev/sdc      // /dev/sdc is the failed disk
# mkdir /tmp/sdc
# mount -r -t reiserfs /dev/loop1 /tmp/sdc
```
[COLOR=#000000][FONT=Arial]I get my folders and files in the /tmp/sdc folder then I can copy some files and folders but at a very slow speed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]When I try to get them from the .dsk file with:[/FONT][/COLOR]
```
# losetup -o 512006144 /dev/loop2 /media/wdnas.dsk      
# mkdir /tmp/dsk
# mount -r -t reiserfs /dev/loop2 /tmp/dsk
```
[COLOR=#000000][FONT=Arial]In the mount command I got:[/FONT][/COLOR]
```
mount: /dev/loop2: can't read superblock
```
[COLOR=#000000][FONT=Arial]How can I fix that?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I compared the disk content and the .dsk file in a hexadecimal editor and they look the same![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Ref: [http://tristanscott.co.uk/computers/western-digital-netcenter-nas-data-recovery/](http://tristanscott.co.uk/computers/western-digital-netcenter-nas-data-recovery/)[/FONT][/COLOR]

---

