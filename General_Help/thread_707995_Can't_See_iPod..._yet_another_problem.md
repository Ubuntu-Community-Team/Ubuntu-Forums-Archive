---
title: "Can't See iPod... yet another problem"
date: 2008-02-25
forum: General Help
---

### Post by mb184 on 2008-02-25
I have an iPod 5g and i have been messing around with it and i discovered the problem of iTunesLock preventing me from accessing the iPod and putting itself back on.  Well in a stroke of genius I deleted the Play Counts file also trying to see if that would stop iTunesLock from reappearing every time i plug in my iPod.  
Now my computer (ubuntu 7.10) does not see it at all.  Also windows does not see it, until i remove it then it says my iPod is corrupted, but when i connect it, iTunes denies any knowledge of seeing it.

i know there is a .Trash-matthew file on the iPod and i have a great suspicion that if i can get on the iPod and see the hidden files then i could just put the file back.

The dmesg | tail prints:
matthew@matthew-laptop:~$ dmesg | tail
[ 4127.628000] scsi 9:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 4127.632000] sd 9:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[ 4127.632000] sd 9:0:0:0: [sdb] Write Protect is off
[ 4127.632000] sd 9:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 4127.632000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 4127.632000] sd 9:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[ 4127.636000] sd 9:0:0:0: [sdb] Write Protect is off
[ 4127.636000] sd 9:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 4127.636000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 4127.636000]  sdb:

Is there anyway i can force a restore on it in windows, or fix it in linux?

Thanks,
Matt

---

