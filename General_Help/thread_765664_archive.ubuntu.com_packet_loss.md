---
title: "archive.ubuntu.com packet loss"
date: 2008-04-24
forum: General Help
---

### Post by masticate on 2008-04-24
Hi all,

I am noticing packet losses with some of the ubuntu sites. I don't think the issue is with my home network as there are no packet losses with google.com and yahoo.com.

I am testing using a simple "**ping archive.ubuntu.com**" command.

Any one else experiencing similar errors?

> 
--- archive.ubuntu.com ping statistics ---
41 packets transmitted, 34 received, 17% packet loss, time 40020ms
rtt min/avg/max/mdev = 114.890/122.493/154.410/7.945 ms



> 
--- security.ubuntu.com ping statistics ---
76 packets transmitted, 74 received, 2% packet loss, time 75004ms
rtt min/avg/max/mdev = 112.413/114.918/125.929/2.165 ms



> 
--- [www.l.google.com](www.l.google.com) ping statistics ---
81 packets transmitted, 81 received, 0% packet loss, time 80033ms
rtt min/avg/max/mdev = 32.194/34.886/44.586/2.143 ms


---

### Post by xaenyx on 2008-04-24
Yeah, using apt-get some repos time out (archive.ubuntu.com).

---

### Post by masticate on 2008-04-24
I filed a bug report.

[https://bugs.launchpad.net/ubuntu/+bug/221589](https://bugs.launchpad.net/ubuntu/+bug/221589)

---

### Post by wormeyman on 2008-04-24
I can confirm however i think it's just stress due to everyone upgrading.

---

### Post by xaenyx on 2008-04-24
They should throttle core packages in the ahrdy upgrade...  50 people getting 100 kbps is better than 500 getting 10.  Heck, I've been running ubuntu hardy since beta 3, and when I was updating today it stopped updating due to timeout/paket loss, and now everything is broken to the point where I can only use failsafe terminal and launch firefox that way >.<

---

### Post by masticate on 2008-04-24
The bug report has been closed.


> 
In case you hadn't noticed, Ubuntu hardy has just been released, and
bandwidth is somewhat taxed to the Canonical servers. I think in this
instance, packet loss is to be expected.

** Changed in: ubuntu
      Status: New => Won't Fix


---

### Post by juan@forum on 2008-04-24
this is no bug

it is what happened when everyone wants to get their hands on something great at the same time...

---

### Post by chatrang on 2008-11-02
I have a slow connection now matter what site I do to.  Even something as small as the Google homepage.

I ping google.com and I get a 20% packet loss.

I am using a broadcom wmp300n with the driver that came with Ubuntu 8.10.

---

