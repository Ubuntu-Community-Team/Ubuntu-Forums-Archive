---
title: "Mounted NTFS drive, Cannot Write"
date: 2007-01-22
forum: General Help
---

### Post by cielo23 on 2007-01-22
Alright, 

I'm a fairly new Linux ( Ubuntu Dapper 6.06 ) user, but I wouldn't say I'm completely a novice.  I have a dual booted system with Windows XP and Ubuntu.  I have two hard drives in my system. The second drive is the one that contains all my music.  When I try to add files to the drive it tells me that I'm not the owner, so I logged in as root and it still tells me I'm not allowed change anything on the drive when I try to alter permissions.....What am I doing wrong so that I can use this drive? Does it have to do with NTFS? 

Thanks!   ](*,)

---

### Post by Stemp on 2007-01-22
You can't write data on ntfs with the normal ntfs drivers.
For writing you need the ntfs-3g drivers : [How-to NTFS-3G]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g")

---

### Post by cielo23 on 2007-01-22
Oh, alright. Thanks! I'll try that!

---

### Post by cielo23 on 2007-01-22
Is it possible to covert from NTFS to ext3 without losing any data ????

Also can WIN XP read ext3 ?

---

### Post by Stemp on 2007-01-22
> Is it possible to covert from NTFS to ext3 without losing any data ????

I don't know, but I really don't think so.

```
Also can WIN XP read ext3 
```

Yes, there is a software/driver Ext2fs for Windows

---

