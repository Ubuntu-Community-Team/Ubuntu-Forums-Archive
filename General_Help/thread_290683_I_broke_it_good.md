---
title: "I broke it good"
date: 2006-11-01
forum: General Help
---

### Post by wikki on 2006-11-01
Ok, so my box won't boot now.  Here is what I think I did.

I upgraded to Edgy, everything's cool so far.  I was then upgrading some stuff with apt-get and it was telling me that there were some packages that I could delete.  I think one of them was "init something" which I thought sounded reasonable to delete since we're supposed to be using upstart now.  So a day or so later I rebooted my box and now it says /usr/sbin/init is missing and it just drops me to a busybox prompt.  

I know I could just reinstall and restore my home dir from backups, but is there a repair utility or something I could do to fix it a little faster?  

wikki

---

### Post by RjBanker18 on 2006-11-01
Hey wikki, I noticed with my laptop after an upgrade to Edgy, init was still being used.  I assume yours was still using init too.  But I'm sorry I can't help more, anyone know why after an upgrade init is still being used?

---

### Post by Old Pink on 2006-11-01
Just copy /usr/sbin/init from the backup into the directory.

Boot to prompt, and type ```
sudo cp /path/to/backup/usr/sbin/init /usr/sbin/init
```

---

### Post by wikki on 2006-11-01
Thanks old pink.  I was wondering if that would work.  I don't back that up but I guess I can just get it off of the boot cd.  I wish I could remember the name of the package so that I can reinstall it.

Any idea why there are some packages that it says aren't being used and can be removed?

---

### Post by wikki on 2006-11-01
I'm back up. Yay

---

