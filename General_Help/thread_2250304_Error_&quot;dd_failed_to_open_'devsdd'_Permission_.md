---
title: "Error: &quot;dd: failed to open '/dev/sdd': Permission denied&quot;"
date: 2014-10-27
forum: General Help
---

### Post by steve169 on 2014-10-27
I boot and run Lubuntu 14.10 from a 16-gigabyte thumb drive (/sdc).

I want to copy everything to a 32-gigabyte thumb drive (/sdd) so I can boot from it.

Both are Kingston Data Traveler thumb drives, and both are formatted ext4. The larger thumb drive contains one partition, which is blank.

I boot Lubuntu from my live DVD, then plug in both thumb drives and use this command in terminal:  dd if=/dev/sdd of=/dev/sdc bs=512k

I consistently receive this error message:  "dd: failed to open '/dev/sdd': Permission denied"

I'm an experienced Windows user but a raw newbie when it comes to Lubuntu.

What am I doing wrong?

---

### Post by deadflowr on 2014-10-28
Duplicate thread
See
[http://ubuntuforums.org/showthread.php?t=2250302](http://ubuntuforums.org/showthread.php?t=2250302)

This one is closed

---

