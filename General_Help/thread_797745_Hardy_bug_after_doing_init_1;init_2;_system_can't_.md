---
title: "Hardy bug: after doing init 1;init 2; system can't see USB drives"
date: 2008-05-17
forum: General Help
---

### Post by descentspb on 2008-05-17
So this is my problem. After doing init 1 and then init 2 (i believe that's the reason) the system does not see the plugged in USB-HDD (or USB-flash). And the only way i can solve is just to restart the system!
Also i can't mount it manually cause "fdisk -l" does not show me the new drive.

That's the output of "dmesg | tail" (kernel 2.6.24-16-rt):
```
[136712.186992] sd 13:0:0:0: [sdc] Mode Sense: 00 00 00 00
[136712.186994] sd 13:0:0:0: [sdc] Assuming drive cache: write through
[136712.187991] sd 13:0:0:0: [sdc] 117210240 512-byte hardware sectors (60012 MB)
[136712.188737] sd 13:0:0:0: [sdc] Write Protect is off
[136712.188740] sd 13:0:0:0: [sdc] Mode Sense: 00 00 00 00
[136712.188741] sd 13:0:0:0: [sdc] Assuming drive cache: write through
[136712.188743]  sdc: sdc1
[136712.232652] sd 13:0:0:0: [sdc] Attached SCSI disk
[136712.232682] sd 13:0:0:0: Attached scsi generic sg3 type 0
```

I don't know if that matters but restarting dbus also doesn't help.

Please, help me to solve it!

---

### Post by descentspb on 2008-05-18
bump

---

### Post by rrwo on 2008-05-19
I've noticed that I've been having hte same problem.

---

### Post by descentspb on 2008-05-19
hey, that's not right! This becomes a confirmed bug. Please, add your confirmation here: [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/231462](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/231462)
Let's hope someone helps us.
Though the only reason i often switch to init 1, is the buggy Hardy. This ususally helps.

---

