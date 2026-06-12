---
title: "pysdm"
date: 2006-11-03
forum: General Help
---

### Post by blindmist on 2006-11-03
so i installed pysdm hoping to be able to see my NTFS partition. everyone said it works.

it mounted just fine, but when i go to open the folder, it says that i dont have permission to view the contents.

any help?

---

### Post by TigerWolf on 2006-11-03
How did you mount it?

Ubuntu already has its own read only mounting "software" for ntfs and there is also ntsf-3g for write support. 

I dont know anything about pysdm

---

### Post by blindmist on 2006-11-03
just mounted it with the default settings in pysdm

---

### Post by TigerWolf on 2006-11-03
Could you type this command - ```
gedit /etc/fstab
``` and copy the contents and paste it here?

---

### Post by blindmist on 2006-11-03
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/hda1
UUID=a4d9b8ad-f003-4728-8a40-f51c99969b0b  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/hda5
UUID=b35029ba-52ba-4060-9309-61f938ac6cc3  none            swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/hdd                                   /media/cdrom1   udf,iso9660  user,noauto                 0  0  
/dev/                                      /media/floppy0  auto         rw,user,noauto              0  0  
/dev/hdb1                                  /media/windows  ntfs         defaults                    0  0  
/dev/hda1                                  /media/hda1     ext3         defaults                    0  0  
/dev/hda5                                  /media/hda5     swap         defaults                    0  0  
/dev/hdb                                   /media/windows  ntfs         umask=0222                  0  0  

```

---

