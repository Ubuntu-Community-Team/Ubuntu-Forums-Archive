---
title: "HELP power surge killed my computer"
date: 2007-09-30
forum: General Help
---

### Post by x1a4 on 2007-09-30
Hi,

I had a massive power surge that killed my power supply.  When I replaced it things worked until I selected what to boot at the grub menu and got the following error: 'Error 16: Inconsistant filesystem structure'

So I booted to the cd and ran fsck on all file systems and they all check out.  What else can I try to diagnose and fix the problem?  Preferably without having to reinstall.  I am able to mount and access all file systems from the livecd.

Thank you.

Here are the fsck results: 
```

root@1[root]# fsck /dev/hda1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda1: clean, 63/262144 files, 29602/524112 blocks
root@1[root]# fsck /dev/hda2
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda2: clean, 13160/8273920 files, 7097694/16522852 blocks
root@1[root]# fsck /dev/hda5
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda5: clean, 24/524288 files, 34931/1048233 blocks
root@1[root]# fsck /dev/hda6
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda6: clean, 223/524288 files, 35581/1048233 blocks

```

EDIT: I also get a "Unknown Flash Type" BIOS error.  Could that be the cause or part of the problem or something else?

---

### Post by x1a4 on 2007-09-30
Okay, I fixed it.  Some of grub's files, probably stage2 as it threw the error just after I selected what to boot, got corrupted--why I was able to access the drive from the livecd.  I replaced grub from backups and things are peachy.  

I now have to figure out what that 'Unknown Flash Type' error is and how to fix it and I'll be rock 'n' rollin'

---

