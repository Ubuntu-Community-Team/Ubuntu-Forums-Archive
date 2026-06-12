---
title: "&quot;a start job is running for dev-disk-by....&quot; for 1 minute 30 seconds"
date: 2016-06-22
forum: General Help
---

### Post by scottbomb on 2016-06-22
Recent install of 16.04. I was wondering why it took the machine so long to boot so I turned off "quiet splash" in grub. Now I see some sort of startup "job" that is delaying startup by exactly 1 min. 30 seconds... every time.

```
A start job is running for dev-disk-by\x2uuid-c5cc ... .device"
```

Anyone know what this is and how to fix it?

---

### Post by Dennis N on 2016-06-23
I would investigate what device this is. Is your code shown complete and correct? Partitions are referenced by **/dev/disk/by-uuid/<some UUID>**. It might be a partition where the UUID has been changed for some reason or perhaps no longer exists.

Use the command **sudo blkid** to see if anything matches the UUID displayed in the message. You could have a wrong UUID in your /etc/fstab.

The 90 seconds is the systemd default timeout, which can be changed, but changing the timeout time does not solve the problem.

---

### Post by scottbomb on 2016-06-25
I hate to say it, but something went wrong on that machine the other day and I had to reformat. I'll close this question for now.  Thank you for the response. I wish I could test it.

---

