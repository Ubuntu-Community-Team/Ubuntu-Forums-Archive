---
title: "Remote gkrellm?"
date: 2004-11-26
forum: General Help
---

### Post by quackking on 2004-11-26
First : What a great distro! Thanks, to whoever has put in time!  :grin:  This is my first debian experience; I am mostly familiar with Mandrake (also a good distro)

My question is this: I have gotten gkrellm and lm-sensors working, but only locally (I can see it on my own desktop.) I can't seem to connect to the gkrellmd daemon from any other machine, though. I have installed Webmin (1.170) and Webmin-iptables, and set up a firewall which passes port 19150, which should be what gkrellmd needs, but no luck. In fact, I can't connect even if iptables is turned off!

Any idea what I am doing wrong? On my Mandrake boxen this works without any configuration at all. 

Thanks in advance!

---

### Post by quackking on 2004-11-26
Oh yeah - I can connect to other services fine, including Webmin (of course) on port 10000, httpd, ssh, tightvnc, etc. It is not a connectivity problem.

---

### Post by quackking on 2004-11-26
HAH! - sorry, I was an idiot. By default the other (Mandrake) systems do not have any entries in /etc/gkrellmd.conf, which leaves them wide open. Ubuntu starts with only 127.0.0.1 available. 

Problem solved. RTconfig file next time...

---

