---
title: "Cannot mount UFS DVD as user"
date: 2007-02-22
forum: General Help
---

### Post by getaceres on 2007-02-22
I have some UDF DVDs that I burned with Nero on Windows. When I enter them in the DVD drive they don't get automounted but a DVD drive appears in Nautilus. When I double-click in it, I get the following:

```

mount: dispositivo de bloques /dev/hdd está protegido contra escritura; se monta como sólo lectura 
mount: tipo de sistema de ficheros incorrecto, opción incorrecta, 
       superbloque incorrecto en /dev/hdd, falta la página de códigos, 
       o algún otro error 
       en algunos casos se encuentra información en syslog, pruebe 
   dmesg | tail   o algo parecido 

```
Sorry about the spanish message. It says that it cannot mount /dev/hdd because if finds a not valid filesystem.
This is dmesg|tail info:

```

.....
[17188926.564000] Unable to identify CD-ROM format.
[17188993.952000] Unable to identify CD-ROM format.
.....

```And this is my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=9e9384a1-88b2-4bda-b69e-66aa63383526 /               xfs     defaults        0       1
# /dev/hda2
UUID=b3fb2b98-588f-4070-ad99-a838d790a60a /boot           ext3    defaults,acl,user_xattr        0       2
# /dev/hdb2
UUID=8660-ED06  /media/Juegos   vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hdb1
UUID=4330-75E7  /media/Seguridad_Windows vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda1
UUID=4400404500404062 /media/Windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/hda5
UUID=5a440573-3446-4af8-bcc0-b05c24f99bc3 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb3       /media/Seguridad_Linux  ext3    defaults,acl,user_xattr 0       2

```However, the most strange thing is that if I run 

```

sudo mount -t udf /dev/hdd /media/cdrom1

```It gets mounted!!! Why? Is there some kind of privilege limitation when trying to mount an UDF DVD?

---

