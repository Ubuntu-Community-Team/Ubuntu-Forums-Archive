---
title: "Truecrypt partition mounts as root"
date: 2007-08-09
forum: General Help
---

### Post by Paradigm_Complex on 2007-08-09
When I mount my truecrypt partition, it ends up being owned by root.  Trying to change it to my user with chown throws out errors.  This forces me to use root privileges to access it every time.  Each time I copy something off of it I have to chown it.

If anyone could help me in getting the truecrypt partition to user rather then root, I'd be very appreciative.

---

### Post by SelrahCharleS on 2008-01-13
I'm not sure if this is your problem but if your volume is formatted as FAT you have to mount it with the -u flag for it to be user writable.

```
sudo truecrypt -u myvolume /mnt/myencryptedstuff/
```

That should do the trick.

---

