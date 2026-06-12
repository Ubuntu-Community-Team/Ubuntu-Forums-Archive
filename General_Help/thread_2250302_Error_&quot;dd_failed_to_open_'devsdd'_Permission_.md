---
title: "Error: &quot;dd: failed to open '/dev/sdd': Permission denied&quot;"
date: 2014-10-27
forum: General Help
---

### Post by steve169 on 2014-10-27
I have the latest version of Lubuntu installed on a bootable 16 GB flash drive (/sdc). I want to copy everything to a 32 GB flash drive (/sdd). Both are Kingston Data Traveler thumb drives, and both are formatted ext4.

I boot Lubuntu using my live DVD, then insert both thumb drives.

I use this command in terminal:  dd if=/dev/sdd of=/dev/sdc bs=512k

I consistently get this error message:  dd: failed to open '/dev/sdd': Permission denied

I'm a raw newbie. What am I doing wrong?

---

### Post by Dennis N on 2014-10-27
You need to use **sudo** to run that.

---

### Post by yancek on 2014-10-28
Your command is reversed.  If you want to copy from sdc to sdd  you need:

>   dd if=/dev/sdc of=/dev/sdd bs=512k

---

### Post by steve169 on 2014-11-10
Got it. Many thanks.

---

### Post by bapoumba on 2014-11-10
Please mark your thread as solved (under Thread tools), thanks.

---

