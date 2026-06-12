---
title: "Trouble with deluge/firewall?"
date: 2007-11-21
forum: General Help
---

### Post by Hybrid86 on 2007-11-21
Very few torrents ever start to download, and when they do, the number of seeders listed is much smaller than the site said were there (126 according to mininova vs 9 according to deluge). I made a rule in firestarter allowing ports 6881-6889, but that doesn't seem to help.

Does anyone know how to fix this issue? :confused:

---

### Post by stomponthis on 2007-11-21
In Deluge go to
EDIT- Preferences - Network - "TEST ACTIVE PORT"
If the result is OK then its not your ports
Sound funny to use multiple ports, I just use one?

Also try the bandwidth section to configure you download.  When I installed it had low settings for maximum connections etc.

---

### Post by Hybrid86 on 2007-11-21
Test active port gave me this:
```
TCP port 6881 closed on xx.xxx.xx.xxx
```

---

### Post by por100pre1 on 2007-11-21
> **Hybrid86 said:**
> Test active port gave me this:
```
TCP port 6881 closed on xx.xxx.xx.xxx
```

Is your PC behind a router? If yes try opening the ports in the router firewall.

---

### Post by NineseveN on 2007-11-21
I ran into something that might be similar when I installed Azureus. I had my hardware router/firewall set up to port-forward for Azureus on my Windows XP which uses a static IP.

When I installed Ubuntu, it defaulted me to an IP address that was different than the one I assigned in Windows XP. Since my services and port-forwarding are mapped to a certain IP (the one I use in XP), when I tried to run Azureus, the ports did not work (because I wasn't suing the IP address that I set it up for).

I had to go into the network settings in Ubuntu and change my IP to static, put in the right IP (it had the right default gateway) and then add my primary and secondary DNS addresses.

Once I did that, Azureus ran like a charm (better than it did in Windows XP, though that might just be a fluke).

I don't know if this is your issue, but I thought I'd throw it out there as something to try. I've never tried Deluge, but I would think that this issue could affect any similar software. make sure your services/port-forwarding is setup correctly in your Router/Firewall (if you have one).

---

