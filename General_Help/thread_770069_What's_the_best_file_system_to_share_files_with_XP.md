---
title: "What's the best file system to share files with XP?"
date: 2008-04-27
forum: General Help
---

### Post by evozniak on 2008-04-27
Hello, I'am using 8.04 LTS in my laptop and want share my files with XP, my /home are a XFS file system with large files, isos, movies and misc.

My questions.
  I can use /home as NTFS?
  I can mount XFS partition in XP?

---

### Post by dcstar on 2008-04-27
> **evozniak said:**
> Hello, I'am using 8.04 LTS in my laptop and want share my files with XP, my /home are a XFS file system with large files, isos, movies and misc.

My questions.
  I can use /home as NTFS?
  I can mount XFS partition in XP?

1: No

2: Don't know, there is a EXT3 tool for XP but other Linux FS support may not be that easy.

---

### Post by mahousaru on 2008-04-27
> **dcstar said:**
> 
2: Don't know, there is a EXT3 tool for XP but other Linux FS support may not be that easy.

Ext2IFS works very well for Windows now they have sorted out the UTF-8 support, but it will BSOD the machine if you mix it with TrueCrypt.  Its a Ext2IFS issue and I believe it will be fixed in the next release.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by evozniak on 2008-04-27
thanks for advice
i'am going format my /home as EXT3 and wait for new release of this Ext2IFS.

---

