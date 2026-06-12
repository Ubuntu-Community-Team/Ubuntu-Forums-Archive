---
title: "Installed lm-sensors and lost all network connectivity"
date: 2008-06-07
forum: General Help
---

### Post by awilki01 on 2008-06-07
I installed lm-sensors to try and monitor my hardware temp, etc.  Now, I have no network connectivity....

When I try to ping my directly connected default gateway, I get the following:

```

ping: sendmsg: Operation not permitted

```

I have even removed lm-sensors, removed the entries it made in the /etc/modules file and rebooted to no avail.

My eth0 interface is up and has an IP address.  I can ping myself and my loopback interface (127.0.0.1), but that is it.  Other PCs on my network are running just fine.  

Something else is that I am running VMWare with a virtual instance of Windows XP on this Linux box and it can reach the network and Internet using the same interface (eth0) my Linux box does.

Any ideas here???

---

### Post by awilki01 on 2008-06-07
Disregard.  It was not lm-sensors.  I had been doing quite a bit today on my Ubuntu box.  It was VMWare.  I fixed the issue.

---

