---
title: "Keeping laptop on WoL"
date: 2013-01-25
forum: General Help
---

### Post by shaaraddalvi on 2013-01-25
Hello everyone,
I have come accross this new exciting feature of WoL (Wake on LAN), and read about it on Wikipedia. I am running Kubuntu 12.04 on an HP Pavilion g6 laptop. I got the concept of WoL, however, I don't know how actually to keep my laptop on WoL mode.
Are there any external packages I need to install on it? I have sudo access for laptop.
Thanks in advance.. :)

---

### Post by tgalati4 on 2013-01-25
Search for acpitool and ethtool on the forums.  You need to turn on the WoL feature of your network card.  Only works for wired connection, not wireless.  Install ethtool and read the man page.  Install acpitool if you need it to leave power on to certain parts of the bus that has the ethernet card.

---

