---
title: "After new kernel, no ZFS"
date: 2017-12-18
forum: General Help
---

### Post by wintermute000 on 2017-12-18
HELP! I was running ZFS happily and decided to apt-get update  && apt-get upgrade.
Now, after upgrading to 4.10.0-28-generic I no longer have ZFS.

```
root@corebox:/vault# zfs status
The ZFS modules are not loaded.
Try running '/sbin/modprobe zfs' as root to load them.
root@corebox:/vault# /sbin/modprobe zfs
modprobe: ERROR: could not insert 'zfs': Invalid argument
```

I have tried uninstalling and reinstalling zfs using apt, installing zfs-dkms (which I then realised was old advice I think? so I removed). No dice. 

I've lost access to all my storage, so would really love some advice here...

---

### Post by wintermute000 on 2017-12-18
OK i'm an idiot. I made some changes to zfs.conf and that was breaking it. Saw the error onthe console when I hooked up a monitor. DOH

removed the offending lines and rebooted, pools back (phew)

---

