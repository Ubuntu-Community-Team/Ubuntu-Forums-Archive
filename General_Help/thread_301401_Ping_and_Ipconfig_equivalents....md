---
title: "Ping and Ipconfig equivalents..."
date: 2006-11-17
forum: General Help
---

### Post by CPtAJ on 2006-11-17
Hey there guys, I was wondering if you could help me out here.

What are the typical linux alternatives for the ping and ipconfig commands one would use on windows/dos? My ISP is having some issues and I need to release and renew my ip every once in a while (otherwise I have to reboot) in order to get the connection back up.

I would normally just type "ipconfig /release" and "/renew" on DOS. Need to do it on linux now.

Pinging would also be helpful for testing pourposes :) 

Thanks dudes.

---

### Post by Joe_CoT on 2006-11-17
the equivalent to ipconfig is ifconfig.

Run ifconfig. It should give you a list of your interfaces. Most likely, your ethernet card is called eth0. To release your ip:
```
sudo ifdown eth0
```

to renew your ip

```
sudo ifup eth0
```

---

### Post by CPtAJ on 2006-11-17
Thanks, dude. Owe you one ;)

---

### Post by dcstar on 2006-11-17
> **CPtAJ said:**
> 
......
I would normally just type "ipconfig /release" and "/renew" on DOS. Need to do it on linux now.


```
sudo dhclient -r
sudo dhclient -l
```

---

### Post by ShagzModo on 2006-11-17
I usually use commandline, but note that the standard ubuntu installation has network tools that also offer ping, trace route, finger, nslookup etc. I taught my girlfriend what they do, she troubleshoots with these tools... very nice!

rgds,

Shagzmodo

---

