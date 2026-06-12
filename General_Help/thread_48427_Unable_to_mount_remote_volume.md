---
title: "Unable to mount remote volume"
date: 2005-07-12
forum: General Help
---

### Post by mikeb on 2005-07-12
I am trying to mount a volume on my OS X machine on Ubuntu. Following instructions in the unofficial guide, I've installed everything and configured everything (I think). When using the command recommended in the guide (sudo mount //192.168.0.1/linux /media/sharename/ -o username=myusername,password=mypassword), I discovered that Ubuntu is trying to connect to port 445, but the OS X firewall is configured to use ports 548 and 427 for file sharing.

So, when I issue the command without port number, I get an error report referring to port 445. When I modify the command so: 'sudo mount //192.168.0.1:548/linux /media/sharename/ -o username=myusername,password=mypassword', I then get a different error saying 'can't find address for //192.168.0.1'

How can I solve this problem?

---

### Post by lartan on 2005-07-23
Hi,

I'm trying to do the same and am wondering if you have had any progress on this issue??
Thanx!
Arne

---

