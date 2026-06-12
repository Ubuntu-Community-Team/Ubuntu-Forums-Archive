---
title: "fsck taking to long"
date: 2007-01-20
forum: General Help
---

### Post by Wolf359T on 2007-01-20
I have a mounted fat32 partition with 192G in size. Every time Ubuntu boots, the fsck is checking my partitions (including the big 192GB one) and takes to much time. How can I tell fsck to check every 30 days or so, or every 100 boots? It's very annoying waiting a few minutes for fsck after each system reset.

---

### Post by mcduck on 2007-01-20
could you post your /etc/fstab here?

---

### Post by icehammer on 2007-01-20
Same here.. it takes too bloody long.. and ends up with: 

1. Differences in boot sector and its backup.. NOT automatically fixing this.
2. Something with cluster count.. Shows all my fat32 drives and clusters in each.. with another qty which i can't figure out..
3. Ends with: "fsck died with exit status 1".

Tell me if u find out an effective solution..
Copy of /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda9
UUID=227cb2fd-ab9c-4adc-b227-a6615d1b43ab /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=6C61-3195  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=F4C0-F226  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=58C9-5FC5  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=345E-624F  /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda8
UUID=F414-6475  /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=800C-8EE9  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=5881-1F1B  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=9C49-E4EB  /media/hdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=E84C-1A32  /media/hdb7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda10
UUID=231ca25d-f361-42aa-9514-0be3afa3188d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Wolf359T on 2007-01-20
Here's mine:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=071b6ee0-9ba8-409a-83e7-b6c1ec78a721 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=A8A86B81A86B4D3E /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=4453-A279  /media/hda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=47cd72af-13ae-4d89-ab9a-1ccd6cb0c716 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by mcduck on 2007-01-20
Ok, the problem is exactly what I was suspecting. For some reason Edgy's install sometimes seems to set wrong parameters for FAT and NTFS partitions in fstab.

Change the last number in the FAT partition's entry lines from 1 to 0 or 2.

1 should only be used for / partition, all other partitions should have either 2 (to check them *after* root partition) or 0 (to not check them at all).

After doing that your system should boot correctly.

edit: here are the corrected fstabs for you:

icehammer:```
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda9
UUID=227cb2fd-ab9c-4adc-b227-a6615d1b43ab / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1
UUID=6C61-3195 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hda5
UUID=F4C0-F226 /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hda6
UUID=58C9-5FC5 /media/hda6 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hda7
UUID=345E-624F /media/hda7 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hda8
UUID=F414-6475 /media/hda8 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hdb1
UUID=800C-8EE9 /media/hdb1 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hdb5
UUID=5881-1F1B /media/hdb5 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hdb6
UUID=9C49-E4EB /media/hdb6 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hdb7
UUID=E84C-1A32 /media/hdb7 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hda10
UUID=231ca25d-f361-42aa-9514-0be3afa3188d none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
```

Wolf359T:```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc  /proc  proc  defaults  0  0
# /dev/hda5
UUID=071b6ee0-9ba8-409a-83e7-b6c1ec78a721 /  ext3  defaults,errors=remount-ro 0  1
# /dev/hda1
UUID=A8A86B81A86B4D3E /media/hda1  ntfs  defaults,nls=utf8,umask=007,gid=46 0 0
# /dev/hda4
UUID=4453-A279  /media/hda4  vfat  defaults,utf8,umask=007,gid=46 0  0
# /dev/hda6
UUID=47cd72af-13ae-4d89-ab9a-1ccd6cb0c716 none  swap  sw  0  0
/dev/hdd   /media/cdrom0   udf,iso9660 user,noauto  0  0
/dev/  /media/floppy0  auto    rw,user,noauto  0  0
```

---

### Post by Wolf359T on 2007-01-21
Thanks!

---

### Post by henningludeke on 2007-02-16
Worked for me too, thanks :)

---

