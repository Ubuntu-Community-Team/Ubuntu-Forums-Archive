---
title: "Permissions problems NTFS partition"
date: 2008-05-04
forum: General Help
---

### Post by virtuallinux on 2008-05-04
I decided I wanted to share a data partition between XP and Ubuntu.  In Ubuntu, I'm mounting this NTFS partition as /home, and, for the most part, things are working pretty well.  The problem is that all the permissions for all of the files on the drive are 770, with root as owner.  I've tried changing the permissions and the owner, but they refuse to change.  I think the problem is related to the fact that it's an NTFS partition.  

I'm running Hardy Heron, btw. Thanks.

---

### Post by neymac on 2008-05-05
After upgrade from 7.10 to 8.04 I have problems with permissions in NTFS partitions, the owner of those partitions is root and the group is plugdev.
My /etc/fstab is:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d415fac3-d34d-4d91-8501-cf798bbf654c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
# UUID=2A29002C28FFF523 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=1CCFBFF86CFA8BD7 /media/sda4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
# UUID=0a7297af-2bf0-4afb-9e3c-12e716213109 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=86e64e95-2a1c-44f4-9a54-1fa7c893df93 /media/sda6     ext3    defaults        0       2
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

I try change permissions for /media/sda4  (NTFS) partition (using sudo chown ney:ney /media/sda4 ), but it doesn't work and shows no errors.

I can read, execute delete/write files to/from the /media/sda4 partition.

The result of ls -l of /media/sda4 is:
> :/media/sda4$ ls -l
total 1368
drwxrwx--- 1 root plugdev      0 2006-07-22 14:04 Azureus
drwxrwx--- 1 root plugdev  36864 2008-05-04 20:16 cdbom
drwxrwx--- 1 root plugdev  77824 2008-05-04 18:40 Documentos Pessoais
drwxrwx--- 1 root plugdev  53248 2008-04-24 11:22 Filmes
drwxrwx--- 1 root plugdev 532480 2007-01-03 11:25 fotos para trigem
drwxrwx--- 1 root plugdev  12288 2008-01-06 10:18 Imagens
drwxrwx--- 1 root plugdev  32768 2007-08-09 21:10 Instalados
drwxrwx--- 1 root plugdev   4096 2008-01-02 14:28 ISOsImportantes
drwxrwx--- 1 root plugdev  69632 2007-01-24 12:31 Minhas imagens
drwxrwx--- 1 root plugdev      0 2005-08-23 14:02 MSOCache
drwxrwx--- 1 root plugdev 561152 2007-09-09 17:20 Musicas
drwxrwx--- 1 root plugdev      0 2005-03-02 21:37 RECYCLER
drwxrwx--- 1 root plugdev  16384 2007-05-18 16:19 Serial
drwxrwx--- 1 root plugdev   4096 2007-01-24 12:32 System Volume Information

Is there any way to restore the ownership to the user instead of root as it used to be in Ubuntu 7.10 before the upgrade?

The inconvenience of this is when I copy/move files from NTFS partition to my Ubuntu partition, I cannot delete them whithout change the permissions. It is very annoying.

---

### Post by q41 on 2008-11-08
I have the exact same problem. Has anyone of you guys found a solution?

---

### Post by drs305 on 2008-11-08
What you are describing is completely normal. Linux doesn't support NTFS permissions in the usual sense. Ownership of the device is determined at mounting and cannot be changed. Thus, you see 'root' as the owner. With ntfs-3g, reading/writing is fairly seamless, as you both have found. You can read/write to these files without problem even though they are owned by 'root'.

If you really wanted to make them look 'normal', you can specify the owner at mounting by putting them in fstab and including a "uid=1000" or whatever your user id is in the options section.  (In recent versions 'ntfs' is an acceptable substitute for 'ntfs-3g').

Example:
/dev/sdb2 /media/myfiles ntfs-3g auto,users,uid=1000,utf8,umask=027 0 0

---

### Post by q41 on 2008-11-08
Nice, thanks :)
It works perfectly!

---

