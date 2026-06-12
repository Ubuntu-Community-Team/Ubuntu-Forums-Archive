---
title: "Why so many reboots?"
date: 2012-11-07
forum: General Help
---

### Post by Statia on 2012-11-07
The old adage used to be that Linux users only rebooted their computers to add or remove hardware and to upgrade the kernel.
These days however, the system often tells me I have to reboot my system after I have done upgrades that not included the kernel.
Why is this? Laziness by developers? Has it become too hard to temporarily switch to another run-level and/or restart the the X-server?

---

### Post by MG&amp;TL on 2012-11-07
You try telling a new user to restart the X server, or some other obscure service that needs to be restarted due to a new lib*.

Easier just to restart, the old hands know what they're doing anyway.

---

### Post by Statia on 2012-11-07
Can't that be included in the post-install scripts?

```
service foo restart
```

X might be a bit trickier, but I'd think still do-able.

---

### Post by Frogs Hair on 2012-11-07
I have actually seen a decrease since beginning to use Ubuntu. Anything to do with X-server and kernels used to prompt a restart. Now I restarts  mainly with kernel updates. I have installed proposed updates since 10.04 so I don't it it is hardware related or not.

---

### Post by MG&amp;TL on 2012-11-07
Of course, and many do so, but (with the configurability of linux in mind) most present the option. Normally, via the command line, this isn't a problem (select which one you want, deal with consequences). *I think *that update manager just says 'no' to all the service-related questions, but logs a request to reboot. (Need someone better-qualified than me to check this- guys? :) ).

So, to answer your question, probably a mix of developer laziness, and the undesirability to prompt the user to restart (or not restart) a load of services.

How could X be done without dropping out of the user-friendly GUI environment temporarily?

---

### Post by HermanAB on 2012-11-07
Well, lemmesee when last I rebooted my mail/web server:
[root@neptune ~]# uptime
 01:12:14 up 1107 days, 12:18,  2 users,  load average: 0.01, 0.01, 0.00
[root@neptune ~]# echo 'scale=3;1107/365'|bc
3.032

Three years is not exactly many reboots...

---

### Post by Statia on 2012-11-07
So you are running kernel 2.0?

---

