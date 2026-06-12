---
title: "Sudo needed to mount in home directory?"
date: 2017-01-02
forum: General Help
---

### Post by SchnappiJedi on 2017-01-02
Hi,

When mounting a drive in /mnt one has to use 

```
sudo mount -t...
```

If one mounts a drive in users own home directory is sudo still needed?

---

### Post by TheFu on 2017-01-03
Yes.  

mounting is an extremely powerful thing.  IMHO, it should alway require escalated permissions.  With the unrestricted power to mount, you can completely replace the OS and all programs on it.  You can make any/all programs run with root privileges, setup a backdoor, then run the real command so nobody notices.

mounting is extremely powerful.

---

