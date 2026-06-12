---
title: "Update Manager Thinks Network Is Down"
date: 2007-08-23
forum: General Help
---

### Post by cmnorton on 2007-08-23
I have network connectivity -- I am writing this post. I have updated on 6.06 today without a hitch. All of a sudden, there is a network icon where the update manager icon usually appears when there is an update. It shows an orange triangle with a "!", and says there is no network connection.

I restarted /etc/init.d/networking today; that is about all I can think of.

Is this a known bug, or a configuration problem?

Any suggestions would be appreciated.

---

### Post by john8791 on 2007-08-24
> **cmnorton said:**
> I have network connectivity -- I am writing this post. I have updated on 6.06 today without a hitch. All of a sudden, there is a network icon where the update manager icon usually appears when there is an update. It shows an orange triangle with a "!", and says there is no network connection.

I restarted /etc/init.d/networking today; that is about all I can think of.

Is this a known bug, or a configuration problem?

Any suggestions would be appreciated.


Maybe a DNS issue?  Try using [OpenDNS]("http://www.opendns.com").  There servers are:
208.67.222.222
208.67.220.220

Might not have anything to do with your problem but it has fixed some quirky issues I had with Mediacom's DNS servers.

---

