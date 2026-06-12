---
title: "network-manager: connecting to neighbor's network by default!"
date: 2007-02-21
forum: General Help
---

### Post by kpkeerthi on 2007-02-21
After login, network manager connects to my neighbor's network by default. Is there any way I can specify 'preferred network' or force it to always look for my access point, if present?

---

### Post by lhtown on 2007-02-22
There is a program that you can use for wireless networks that will search for available connections. I believe Knetworkmanager is one, but I think there are others.

---

### Post by grado on 2007-11-09
I have a similar problem too. Is there a fix for this problem?

Thanks!

---

### Post by Endolith on 2008-03-27
I have the same problem.  My neighbor's is unsecured and mine is WPA2, so maybe that has something to do with it?  Is there a way to edit nm-applet's configuration to whitelist only my own router?

---

### Post by pointone on 2008-03-27
If you connected to it before, the network manager will add it to the list of networks it automatically tries. I was never able to find a way to prioritize this list, but you can remove it from the list entirely by removing ~/.gconf/system/networking/wireless/networks/<SSID>.

---

### Post by Endolith on 2008-03-27
> **pointone said:**
> If you connected to it before, the network manager will add it to the list of networks it automatically tries. I was never able to find a way to prioritize this list, but you can remove it from the list entirely by removing ~/.gconf/system/networking/wireless/networks/<SSID>.

Very good!  Thank you!

---

### Post by grado on 2008-03-27
Worked! Thank you.

---

