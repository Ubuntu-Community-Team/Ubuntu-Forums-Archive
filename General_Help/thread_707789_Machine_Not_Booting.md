---
title: "Machine Not Booting"
date: 2008-02-25
forum: General Help
---

### Post by redstar1949 on 2008-02-25
please help! I am no longer able to boot my computer. When I boot the computer in recovery mode, I get an error message that says 

"ALERT! /dev/disk/by-uuid/5b2aaca6-44f3-475a-8d36-9530b7a64e79 does not exist. 
Dropping to a shell! 
Check your root= boot arguement (cat /proc/cmdline) Check for missing modules (cat /rpc/cmdline), or device files (ls /dev)" 

what do I do?

---

### Post by Sam Lars on 2008-02-25
You could try looking in your fstab for that number to see what it's not finding...

---

