---
title: "Modifying which server to time synchronise at startup"
date: 2005-09-15
forum: General Help
---

### Post by Ian Green on 2005-09-15
I had set the NTP up in other parts of the system to get the time from any of a few servers within our Intranet, but on startup it kept on delaying at the point where it tries to synchronise the clock with ntp.ubuntulinux.org !  This was confusing, because everywhere I read about how and where to set the time servers I had already done.

After searching I found some posts about an earlier distribution on how to remove that step entirely from the startup, but eventually I found that there is one more place to set time servers, which is the only place that the startup script looks:

sudo nano **/etc/default/ntpdate**

Just comment out the external time server and put in one that you **can** reach locally.

---

### Post by evilghost on 2005-09-15
```

sudo gedit /etc/init.d/ntpdate

```

Line 10, change that to the server of your choice.  It defaults to pool.ntp.org

Hope this helped :)

---

