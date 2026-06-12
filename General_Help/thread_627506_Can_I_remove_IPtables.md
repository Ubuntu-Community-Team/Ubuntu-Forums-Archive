---
title: "Can I remove IPtables?"
date: 2007-11-30
forum: General Help
---

### Post by Naegling23 on 2007-11-30
I've been having problems with iptables and my network


[http://ubuntuforums.org/showthread.php?t=625750]("http://ubuntuforums.org/showthread.php?t=625750")

Im behind a hardware firewall, which I know isnt the best, but at least its something.  When I go to remove iptables, it also wants to remove a package called ubuntu-core or ubuntu-universal or something.  The package discription recommends not removing this packagae due to it handling upgrades or something.  So I have two questions

1) can I safely remove iptables and ubuntu-universal or whatever its called without damaging my system?

2) or is there a way to configure ip tables to allow my network to connect again.

This is sort of urgent, I use my network to back up my data...its been a couple of months....

---

### Post by skymera on 2007-11-30
well IP tables is effectively your firewall , so i wouldnt remove.

configure IP tables with firestarter

sudo apt-get install firestarter

---

### Post by Naegling23 on 2007-11-30
I have firestarter installed, I cant seem to get it configured to allow network traffic though.  Even if I go to stop firewall, I still cant access my netword.  I also cannot access my router from behind iptables.  Basically iptables is causing me a lot of headaches, and I would like to fix, or remove it.

---

### Post by chrisccoulson on 2007-11-30
By default, iptables is configured wide open anyway. What is the output of:
```
sudo iptables -L
```

---

### Post by Lr5 on 2007-11-30
I had problems accessing network at some point, and it turned out that firestarter failed to start properly after kernel update or something and blocked all access to network. Opening firestarter and disabling the firewall gave me access to local area network, but still not to internet. Removing firestarter solved the problem completely.

---

### Post by Naegling23 on 2007-11-30
> **chrisccoulson said:**
> By default, iptables is configured wide open anyway. What is the output of:
```
sudo iptables -L
```

I attached the output of iptables -L to the link in my first post.  I dont know what any of that means though.

The problem started up, so I installed firestarter to try to fix it, it didnt.  I tried stopping the firewall using firstarter, still not working.  I have access to the internet, just not my internal network.

---

