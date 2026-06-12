---
title: "Raid1 and /dev/md0 problems"
date: 2007-02-13
forum: General Help
---

### Post by JeffD on 2007-02-13
I am relatively new to setting up software raid in linux.  I was able to setup a raid1 using two discs.  I used a mknod command to create /dev/md0, then mdadm to configure the raid.  It worked fine, but, when I restart the computer, the /dev/md0 file is gone ( i guess this directory is dynmically created at boot?).

I can re-mknod the /dev/md0 file, and eventually get the raid back up.  How can I make this persistant?

Also, on a related note, I would like to autoload the raid1 kernel module, rather than manually load it each time.

Can anyone give me a pointer?

---

### Post by Medieval_Creations on 2007-02-16
I'm running a raid0 and I'm experiencing this very same problem.

I'm running Feisty (herd4) 64bit.

---

