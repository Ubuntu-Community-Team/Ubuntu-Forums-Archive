---
title: "mounting iso problem, and workaround"
date: 2006-09-29
forum: General Help
---

### Post by Huffers on 2006-09-29
I just tried mounting a cd ISO file using:

```
sudo mount fileName.iso /mnt/cdiso -t iso9660 -o loop
```

and mount said:

```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

"dmesg | tail" said:

```
Unable to identify CD-ROM format.
```

Now I thought that my ISO was corrupt, but I decided to try to get a second opinion first, so I downloaded [winimage](http://www.winimage.com/) and ran it in wine, which actually worked and I was able to extract the files.

Whats up with mount? It mounted other CDs correctly... Could it be to do with the Joliet extensions or something?

---

### Post by morphodone on 2006-09-29
what iso file are you trying to mount?

---

