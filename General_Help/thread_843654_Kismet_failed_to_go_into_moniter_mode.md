---
title: "Kismet failed to go into moniter mode"
date: 2008-06-28
forum: General Help
---

### Post by abuakel on 2008-06-28
I had kismet working perfectly under my integrated intel card ipw2200.. I ended up deleting my drivers for the integrated card and now I'm working on an atheros pc card.
I've tried every possible combination when I tried to configure the source in the kismet.conf file, but none have worked.

This is what I usually get:
```
$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
Source 0 (ath0): Enabling monitor mode for ath5k source interface ath0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.
```

my chipset for the card is AR5213 with AR5112
and when I right click on the wireless to show the connection information it says it's interface is 802.11 WiFi (ath0) and the driver is ath_pci

what am I doing wrong? :confused:

Edit: I added the specification pdf for the atheros card as an attachment

---

### Post by abuakel on 2008-06-28
anyone?

*bump*

---

### Post by abuakel on 2008-06-29
Still no one?
*bump* again

---

### Post by OliW on 2008-11-08
I realise it has been some time since you posted this but I'm interested in using kismet on my ath5k card.

I'm getting an identical error.

---

