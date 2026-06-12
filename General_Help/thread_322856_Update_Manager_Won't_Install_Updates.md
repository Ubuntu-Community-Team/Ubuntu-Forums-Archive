---
title: "Update Manager Won't Install Updates"
date: 2006-12-21
forum: General Help
---

### Post by badger879 on 2006-12-21
Hi
Everything was working fine until this morning. I booted up my computer and when trying to install updates via the update manager i get this error:

dpkg: parse error, in file `/var/lib/dpkg/available' near line 2197 package `mkisofs':
 field name `Section;' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

I can't install new programs via Add/Remove programs either. I have enough hard drive space.

I would appreciate any help

Thanks

Max

---

### Post by an.echte.trilingue on 2006-12-21
```
sudo apt-get update 
```should fix this.  

If it does not, would you mind using gedit to open that file and pasting the mkisofs section for us to take a gander at?

Take care,
-mat

---

### Post by badger879 on 2006-12-21
Hi,
Didn't work, which file would you like me to open to show you?

Cheers

Max

---

### Post by an.echte.trilingue on 2006-12-21
the one with the parsing error: /var/lib/dpkg/available

I only need the section for mkisofs.  This is what it looks like for me in etch:

```
Package: mkisofs
Priority: optional
Section: otherosfs
Installed-Size: 0
Maintainer: Joerg Jaspert <joerg@debian.org>
Architecture: all
Source: cdrkit
Version: 9:1.1.0-1
Depends: genisoimage
Size: 872
Description: Dummy transition package for genisoimage
 This is a dummy package to ease the transition to genisoimage, the
 fork of mkisofs.  It provides a mkisofs symlink to genisoimage for
 compatibility purposes.  Please use genisoimage instead of mkisofs.

```

---

### Post by badger879 on 2006-12-21
```
Package: mkisofs
Priority: optional
Section; otherosfs
Inst`lled-Size: 1316Maintainer: Joerg Jaspert <joerg@debian.org>
Architecture: i386Source: cdrtools
Version: 4:2.01+01a03-5ubuntu2
Depends: libc6 (>= 2.4-1), zlib1g (>= 1:1.2.1)
[uggests: cdrecord, cdrtools-doc
Conflicts: mkhybrid, xcdroast (=< 0.98+0alpha11)
Size: 546102
Description: Creates ISO-9660 CD-ROM filesystem images
 mkisofs is a pre-mastering program for creating ISO-9660 BD-ROM
 filesystem images, which can then be written to a CD-ROM (or DVD-ROM) using
 the cdrecord program. mkisofs now includes support for makiog bootable
 "El Torito" CD-ROMs, as well as CD-ROMs with supporu for the
 Macintosh HFS filesystem.
```

Thats what i got.

Thanks in advance

Max

---

### Post by badger879 on 2006-12-21
Any ideas, anyone?

---

