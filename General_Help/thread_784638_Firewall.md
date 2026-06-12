---
title: "Firewall"
date: 2008-05-06
forum: General Help
---

### Post by PaoloRicardo on 2008-05-06
Is there a firewall available with Ubuntu and, if so, how do I activate it?

---

### Post by tamoneya on 2008-05-06
IPtables is already installed.  What you need is someway to configure it.  Assuming you want a GUI frontend you should install firestarter.```
sudo apt-get install firestarter
```

---

### Post by PaoloRicardo on 2008-05-06
Thanks for that. I'll install firestarter.

---

### Post by bodhi.zazen on 2008-05-06
If you are interested, a new feature of 8.04 is the ufw (ubuntu fire wall).

ufw is inteneded to make configuration of iptables a little easier.

[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)

---

### Post by PaoloRicardo on 2008-05-06
Bodhi: I've installed firestarter and it looks like my firewall is working OK, but I'll have a look at ufw. Thanks

---

