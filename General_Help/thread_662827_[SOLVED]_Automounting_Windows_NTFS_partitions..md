---
title: "[SOLVED] Automounting Windows NTFS partitions."
date: 2008-01-09
forum: General Help
---

### Post by diwas on 2008-01-09
I have 3 NTFS windows' partitions which i want to be automatically mounted during the system startup of Ubuntu 7.10. Does anyone have solution for this?
Thank you.

---

### Post by taurus on 2008-01-09
You need to add three entries in /etc/fstab for those three ntfs partitions.  That's how you mount them automatically each time you boot Ubuntu.  Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

p.s.  Why double post, [http://ubuntuforums.org/showthread.php?t=662736](http://ubuntuforums.org/showthread.php?t=662736)?

---

### Post by forestpixie on 2008-01-09
sudo fdisk -l 

:)

---

### Post by codesplice on 2008-01-09
Install ntfs-3g.  It handles ntfs partitions really well.

---

### Post by diwas on 2008-01-10
Sorry actually i thought that this post couldnt be posted...hehe electricity problem!

---

