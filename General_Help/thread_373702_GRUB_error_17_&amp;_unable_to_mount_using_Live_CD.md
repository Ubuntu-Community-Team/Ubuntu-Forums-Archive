---
title: "GRUB error 17 &amp; unable to mount using Live CD"
date: 2007-03-01
forum: General Help
---

### Post by CauselessEffect on 2007-03-01
Okay so as I went to startup my computer the other day I received an "Error 17" after GRUB loading...

I've researched to find the problem being GRUB is unable to read the file system.  Which somewhat makes sense after, what I'm assuming to be the cause, installing in Windows a program (the name escapes my memory right now) that allowed me to mount my ext3 partition with read and write capabilities.

As I post this I'm being forced to run off my Ubuntu 6.10 Live CD.  I'm pretty computer savvy but it's my first time using Linux and I've only had Ubuntu for a week so I am still pretty unfamiliar with all the commands.

To hopefully help understand my configuration, fdisk -l shows my partitions are set like this:

```

/dev/hda1               1        5954    47825473+   7  HPFS/NTFS
/dev/hda2            5955        6021      538177+  82  Linux swap / Solaris
/dev/hda3   *        6022        7296    10241437+   7  HPFS/NTFS
```

hda1 being my Windows installation, hda2 my swap, and hda3 being Ubuntu.

I seem to be unable to mount my hda3 partition though, despite being able to run fsck /dev/hda3.  I hoped that would correct any file system errors the Windows application may have caused but still no luck.

Any help would be greatly appreciated since I'd prefer not to have to reinstall over my Ubuntu partition.  Thanks!

---

### Post by chewearn on 2007-03-02
Either it is a typo, or something is very wrong.  Your hda3 (ubuntu), which is supposed to be 83 Linux, in shown as 7 HPFS/NTFS.

If it is not a typo, your ubuntu installation is screwed.  You might need to run a partition recovery, which unfortunately, I know nothing about.

---

