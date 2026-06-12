---
title: "Mount error during boot"
date: 2015-08-19
forum: General Help
---

### Post by 2uQ6KKAD on 2015-08-19
Greetings.

I have an ntfs partition that I want to automount on boot. This worked fine for years until I reinstalled Kubuntu about a year ago. Mounting the partition while the system is up works just fine. Only during boot, I get a message saying that there was an error mounting the partition and I need to press "s" to skip it. I checked my fstab and the UUID seems to be correct. The mount options are "defaults,umask=007,gid=46".
I don't remember if I had switched to a newer version of Kubuntu or just reinstalled it, when the problem appeared. I used to just comment the line out in fstab and mount the partition when the system was up, but it keeps bugging me.
Another strange thing is that the error message says that the partition "was" could not be mounted although the partition in question is really called "Datenschredder" (hi, fellow germans! :)  ). 

I am using Kubuntu 14.04 at the moment.

Thanks in advance!

---

### Post by howefield on 2015-08-19
Post the output of... (or at least the relevant lines)

```
cat /etc/fstab
```

---

### Post by 2uQ6KKAD on 2015-08-19
I don't get it. Now it works all of a sudden. 

Before I started this thread, I had checked the partitions UUID with blkid. It showed a different value than that in the fstab, so I changed that, but after rebooting, the error remained. Now I rebooted again and the error is gone! I'm pretty sure I didn't change anything else. Really sorry, man. I guess there's no point in trying to locate an error that is gone.
Thanks anyway.

---

