---
title: "Remove &quot;administrator permission needed to access hard drive&quot;"
date: 2007-08-26
forum: General Help
---

### Post by DennisTT on 2007-08-26
I have an additional hard drive (with Windows and my data) in my computer and when I try to access it for the first time after startup I need to type my password in.  Is there a way to disable this prompt or bypass it someway?

---

### Post by dulbirakan on 2007-08-26
Use NTFS configuration tool. It is available in the repositories.

---

### Post by DennisTT on 2007-08-28
Actually they seem to be 2 FAT32 partitions.  They don't come up on the NTFS Configuration Utility.

---

### Post by bodhi.zazen on 2007-08-28
you need to edit your fstab file and change the options for the fat partitions.

In the options (4th) column use 

uid=1000,gid=100,umask=007

That should set ownership and permissions :)

See these links for details :

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: vfat (FAT) use umask=000

[How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

