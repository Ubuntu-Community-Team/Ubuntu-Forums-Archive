---
title: "Change VNC listening port in Ubuntu Gutsy?"
date: 2007-11-07
forum: General Help
---

### Post by awsutter on 2007-11-07
Hi all,

I've searched around for some time and haven't come up with an answer to this problem. I'm running Ubuntu 7.10 (x86_64) and need to change the default port on which the built-in VNC server ('Remote Desktop') listens. 

I've seen a few threads addressing this issue but nothing seems to have solved my problem. I can open gconf-editor and modify the keys in desktop > gnome > remote access so that alternative_port is, for example, 3389 and use_alternative_port is true. However, even after these changes, my machine is listening and accepts connections on 5900. It's becoming frustrating.

Has anyone experienced similar issues? Have I missed a config file somewhere?

Thanks,
Drew

---

### Post by Skip Da Shu on 2007-11-13
same question here.

---

### Post by misterhaan on 2008-01-16
i spent a LONG time trying to figure this out and finally got something to work for me.  i found two possibilities and will share them both here:

**1.  change the hidden alternative_port setting**

the first way i found didn’t work for me because the port i wanted to use is not between 5000 and 50000.  so really i’m not sure if it works at all, but here’s how it is supposed to work:

run gconf-editor and browse to /desktop/gnome/remote_access.  there are two keys that you need to change.  the first is use_alternative_port — it needs to be checked.  second is alternative_port — change it from 5900 to whatever port you want (note that the description of the key says it has to be between 5000 and 50000 — i suspect this is why it didn’t work for me).  you probably need to log out and log back in, or maybe reboot to have this take effect.

**2.  use iptables to redirect the port you want to use to the default (5900)**

this is a lot more work than the first method, but i had to do it because the first method didn't work for me.  note that while you may be able to forward the port you want from your router to 5900, but then that only works for connections to the wanl (internet) ip, so i do it with iptables.  these commands set iptables to forward port 1234 to port 5900, so you can connect to yourcomputer::1234 over vnc:

```
sudo iptables -A INPUT -i lo -j ACCEPT
sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 4645 -j REDIRECT --to-port 5900
sudo iptables -A INPUT -i eth0 -p tcp --syn --dport 5900 -j ACCEPT
sudo iptables -A INPUT -i eth0 -j REJECT --reject-with icmp-host-prohibited
```

note this is also allowing all local connections (your computer connecting to itself), established connections, and new connections to port 5900, while rejecting all other new connections.

these changes will be lost when you reboot though, so save them to a file with sudo iptables-save > /etc/default/iptables-rules

to get those rules to load at startup, follow the instructions at this thread to set up /etc/init.d/iptables:  [http://ubuntuforums.org/showthread.php?t=19106](http://ubuntuforums.org/showthread.php?t=19106)

---

