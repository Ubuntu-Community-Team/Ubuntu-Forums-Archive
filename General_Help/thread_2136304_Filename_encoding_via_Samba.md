---
title: "Filename encoding via Samba"
date: 2013-04-17
forum: General Help
---

### Post by andyhelloween on 2013-04-17
Hello all,

I have a samba server running on an Ubuntu Server install. When I browse some files from an Ubuntu client using Nautilus, I get:

```
10-Casamiento (Fot&#65533;grafo) (invalid encoding)
```

An "ó" should go where it shows "&#65533;". I already checked the files encoding and it's UTF8, I also tried *convmv*. All files were copied from an NTFS filesystem.

I succeeded by adding the statement *iocharset* to */etc/fstab*:
 
```
mount -t cifs -o username=me,password=######,**iocharset=utf8** //bar/foo /mnt/bar/foo
```

I was just wondering if this is a correct solution. Also, should I use *cifs*? I was using *smbfs*, but that with the addition of *iocharset* apparently killed Nautilus from time to time.

Thanks much for reading,

Regards,
me.

---

