---
title: "Do I need a firewall??"
date: 2008-04-25
forum: General Help
---

### Post by MozBlue on 2008-04-25
Probably sounds like a dumb question but not used Linux in years!

Just installed Ubuntu 8.04, i realise that there's no real need for virus protection but should i be running a firewall? - If so what's best?

---

### Post by dcstar on 2008-04-25
> **MozBlue said:**
> Probably sounds like a dumb question but not used Linux in years!

Just installed Ubuntu 8.04, i realise that there's no real need for virus protection but should i be running a firewall? - If so what's best?

Unless you run a public IP address on your machine (not your modem/router), no.

Most Windows firewalls are to prevent scumware on your machine getting out into the Internet, that is not an issue with Linux.

---

### Post by FredB on 2008-04-25
> **MozBlue said:**
> Probably sounds like a dumb question but not used Linux in years!

Just installed Ubuntu 8.04, i realise that there's no real need for virus protection but should i be running a firewall? - If so what's best?
You have allready one build in the kernel. If you want to tweak it, just use firestarter.

---

### Post by brian_p on 2008-04-25
> **MozBlue said:**
> Probably sounds like a dumb question but not used Linux in years!

Just installed Ubuntu 8.04, i realise that there's no real need for virus protection but should i be running a firewall? - If so what's best?

That install you have just done does not open any ports. No firewall or tweaking of iptables is needed.

---

### Post by kpkeerthi on 2008-04-25
I'm behind a router and one of the first things I did after installing 8.04 was 
```
sudo aptitude purge ufw iptables
```

---

### Post by DBrocks on 2008-04-25
In a fresh install, no ports are open, so you needn't worry. If you want to see what ports you have open, use nmap

```
sudo apt-get install nmap
```
```

nmap YOURMACHINESIPADDRESS
```

---

