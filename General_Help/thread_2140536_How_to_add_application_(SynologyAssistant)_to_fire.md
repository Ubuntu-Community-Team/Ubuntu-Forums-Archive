---
title: "How to add application (SynologyAssistant) to firewall (UFW)"
date: 2013-04-30
forum: General Help
---

### Post by dvenema on 2013-04-30
I have a Synology NAS device (DS112j). It comes with Linux support: a client (SynologyAssistant) to configure the device. After starting the app, it scans my network to find the device. It doesn't find it because I have the standard firewall (UFW) running. When shutting down UFW, the app finds the device instantly.
[http://www.synology.com/support/download.php?lang=us&b=1%20bays&m=DS112j](http://www.synology.com/support/download.php?lang=us&b=1%20bays&m=DS112j)

However, I would like to keep the firewall up and still be able to use the app. Now I read something ([https://help.ubuntu.com/12.04/serverguide/firewall.html](https://help.ubuntu.com/12.04/serverguide/firewall.html)) about application profiles that can be created for UFW. But how to make one for this app?

Or more general: what is the easiest way to add this app to the firewall so that it is allowed network access?

I run 12.04 LTS.

---

### Post by claracc on 2013-04-30
I think the quick way to fix it is to install gufw (in repositories), which is the gui way to control ufw firewall. There you can add rules to the services or programs or ip addresses you want in an easy way.

---

