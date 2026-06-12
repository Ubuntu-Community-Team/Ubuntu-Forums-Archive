---
title: "Mounting Dos partitions with owner &quot;User&quot;"
date: 2008-06-02
forum: General Help
---

### Post by David1000 on 2008-06-02
Ubuntu appears to assign Dos partitions to the owner root.  Can this be changed?  This causes all sorts of difficulties. Or is one meant to work as root?  Hardly seems safe.

---

### Post by mattress on 2008-06-02
This should do it:
```

mount -o uid=YOURUID /dev/dospartition /mnt/mountpoint

```

The YOURUID bit would be the numeric ID of the user you want to mount it
as. 

HTH

m

---

### Post by Rocket2DMn on 2008-06-02
Other filesystems don't have the same type of file permissions that ext3 uses, so it defaults to root.  You can change the owner or read/write permissions with mount options like mattress suggested.  If the drive is internal, you can add/edit the fstab entry, see here for more details on editing fstab - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by David1000 on 2008-06-03
Well, it took me a while, but it finally dawned on me what was happening.  The mysterious uid stands for user id and similarly, gid stands for group id.  In linux, or Ubuntu anyway, the user by default is root.  So one needs to change the user to your own user number.  In my case, I had to add the options uid=1000 and gid=1000.  The mount command ended up being:

UUID=D5C0-9BA2  /home/david/zBackup/BU-Photos vfat  utf8, umask=000, uid=1000, gid=1000      0       2

I still need to change umask to restrict permissions, maybe to 007.
utf8 is, I believe, required to enable the handling of non-english characters.  No doubt I could drop that but it appears to do no harm.

---

