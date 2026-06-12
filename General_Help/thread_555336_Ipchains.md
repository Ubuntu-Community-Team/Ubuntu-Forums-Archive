---
title: "Ipchains"
date: 2007-09-20
forum: General Help
---

### Post by sugan on 2007-09-20
Hi,

I am using Redhat linux. Can any one explain how to set Ipchains and its rules, As i am working in Lan network I have to allow specific users to access my machine without stoping my firewall or ip tables. How to do that.

Pls help!

Regards,
Sugan

---

### Post by Nebby on 2007-09-20
Ipchains is an old version of iptables, so you'd use iptables instead.
You can select what can connect to your computer with Firestarter, which is basically a GUI for iptables.

```

yum install firestarter

```

---

### Post by sugan on 2007-09-20
Hi,

Its fine, As i am working in Lan network I have to allow specific users to access my machine without stoping my firewall or ip tables. How to do that.

Pls help!

Regards,
Sugan

---

### Post by Nebby on 2007-09-21
Do they have static IPs? If so, it's easy enough.
I'm not sure how to do it w/ just IPtables, but if you've got firestarter like I suggested earlier, just go to Policy and add rules to allow those IPs.

---

### Post by mojoman on 2007-09-21
I've recently set up  iptables on my server and I found _[this howto]("http://forums.debian.net/viewtopic.php?t=16166")_ very helpful. It's for Debian but worked excellent on my server running on Dapper. I reckon that iptables, being a generic linux tool (I think), use the same options for Redhat as well but to be sure that you get accurate information you might want to do a search or post a thread in a Redhat forum (ubuntuforums have a _[Fedora/Redhat subforum]("http://ubuntuforums.org/forumdisplay.php?f=162")_. 

Cheers
/mojoman

---

