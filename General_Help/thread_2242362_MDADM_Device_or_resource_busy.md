---
title: "MDADM: Device or resource busy"
date: 2014-09-01
forum: General Help
---

### Post by Spikerok on 2014-09-01
Hello,

I am trying to rebuild raid on the dedicated server because I have a faulty drive.

I have been trying to use:
mdadm --fail /dev/md1 /dev/sdb1
 mdadm --manage /dev/md1 -r /dev/sdb1

but each time command returns:
/dev/sdb1:  Device or resource busy

How can I go about resolving this issue?

---

