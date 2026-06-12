---
title: "samba for vmware dies after hibernate"
date: 2007-08-27
forum: General Help
---

### Post by reader4 on 2007-08-27
I have a working connection between my Ubuntu 7.04 laptop host and VMWare XP client using samba.  However, after I do a suspend or hibernate, the samba connection seems to be lost - I can no longer connect to my Ubuntu host from the XP client.  Restarting samba with ```
/etc/init.d/samba restart
``` does not help.  Neither does restarting networking.  So far, the only solution is to restart the computer entirely.  I don't even mind if there is an inherent problem after hibernation, but is there a better way to fix the connection without restarting the computer?

---

### Post by eboulet on 2008-01-21
Hi,

I'm having the same problem.

If you restart de vmware daemon you will be able to reactivate samba without rebooting.
(it's working for me)

```
:~$ sudo /etc/init.d/vmware restart
```

hope this helps

---

