---
title: "Configuring local DNS caching (port 53 already in use) 12.04"
date: 2013-07-10
forum: General Help
---

### Post by psfal on 2013-07-10
I'm trying to (tried a couple of times already) install dnsmasq to cache a couple of dns addresses locally for my ping-time dependent games. I get the message that port 53 is already in use. How do I disable it and install dnsmasq? I've already had to completely re-install 12.04 two times because I don't know how to undo the damage done by a  botched install. I'm not a nuts&bolts Linux user but I love my Linux. This tutorial "[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)" doesn't work if port 53 is in use.

Thanks, I hope someone knows the answer to this (no guesses please) If there is a tutorial on this subject, point me in that direction, I've not been able to find one that specifically addresses my issue. (close only counts in horse-shoes)

---

### Post by SeijiSensei on 2013-07-10
Add the addresses and hostnames to /etc/hosts.  It's faster than DNS.

---

### Post by btindie on 2013-07-10
You can use the following to see what's currently listening on UDP:53
```
sudo lsof -Pn -iUDP:53
```

---

### Post by psfal on 2013-07-10
Thanks Seiji, that dropped my ping from 139ms to 17ms without having to do surgery, I'll try that for awhile. Much obliged:-)

---

### Post by psfal on 2013-07-10
Thanks for your answer btindie, the output 
(COMMAND  PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dnsmasq 1772 nobody    4w  IPv4  13313      0t0  UDP 127.0.0.1:53)
 doesn't actually mean anything to me, I want to disable whatever is using the port, (presumably Ubuntu's idea of what's best for dns caching) and install dnsmasq so I can get a 0ms ping-time. Seiji's instructions got me down to 17ms and that's better than I had but I'd still like to get it faster if at all possible. I'll play with it with the 17ms and see if that's enough of an improvement though and possibly leave it at that. It would be nice to know how to proceed if I want to though:-)

---

