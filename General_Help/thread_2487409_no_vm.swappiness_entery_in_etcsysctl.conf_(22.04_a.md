---
title: "no vm.swappiness entery in /etc/sysctl.conf (22.04 and 18.04)"
date: 2023-06-03
forum: General Help
---

### Post by funkytwig4 on 2023-06-03
Want to reduce use of swap space but there is no vm.swappiness entery in /etc/sysctl.conf (did a grep recursive grep in /etc for swappiness and got no hits).

I am using 22.04 and 18.04 and it does not seem to be there on either boxes. 

How do I reduce swap usage?

---

### Post by jeremy31 on 2023-06-03
You add the entry to the bottom of the /etc/sysctl.conf file

---

### Post by exploder on 2023-06-03
Some very good info here.

[https://easylinuxtipsproject.blogspot.com/p/speed-mint.html](https://easylinuxtipsproject.blogspot.com/p/speed-mint.html)

---

### Post by TheFu on 2023-06-03
> **funkytwig4 said:**
> Want to reduce use of swap space but there is no vm.swappiness entery in /etc/sysctl.conf (did a grep recursive grep in /etc for swappiness and got no hits).

I am using 22.04 and 18.04 and it does not seem to be there on either boxes. 

How do I reduce swap usage?

Just because an entry doesn't exist, that doesn't mean it isn't valid.  Create it.  When I first started using Unix, this aspect confused me until someone pointed it out.  It happens all the time.  Not all config files include every possible entry allowed.  Especially when it comes to kernel parameters, there are thousands.  If you've read up on the entry and it doesn't exist, add it with the value you feel is best.  I always add a TAG/comment for every file that I manually change in /etc/ to ensure those changes will be reset from my backups (which always include everything in /etc/) should I need to restore from a backup or migrate to a new install on new hardware.

---

