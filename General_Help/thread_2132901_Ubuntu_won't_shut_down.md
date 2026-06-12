---
title: "Ubuntu won't shut down"
date: 2013-04-06
forum: General Help
---

### Post by jackofall1232 on 2013-04-06
I am getting a bug report that wont let my computer shut down. it is an HP  g7

usb 1-1: >cleartt 1 (9032) error -19
ieee80211 phy0: >brcmsmac: brcms_ops_bss-info_changed: disassociated
ieee80211 phy0: >brcms_ops_bss_info:changed : arp filtering:enable false, count 1 (impliment)
ieee80211 phy0: >brcms_ops_bss_info:changed: qos enabled:fals (implement)
ieee80211 phy0: >w10: brcms_b_coreset:dma_txreset [3] : cannot stop dma
ieee80211 phy0: >w10: brcms_b_coreset:dma_rxreset [0] : cannot stop dma

---

### Post by praseodym on 2013-04-06
Any USB-device plugged in?

> ```
 usb 1-1: >cleartt 1 (9032) error -19
```

---

### Post by wlee1970 on 2013-04-06
have you tried reboot or shutdown -r now?

---

### Post by glln0v on 2013-04-06
open terminal and try: **sudo shutdown -P 0**

---

### Post by wildmanne39 on 2013-04-06
*Thread moved to **General Help**.*

---

### Post by jackofall1232 on 2013-04-06
no usb device [COLOR=#000000] [/COLOR][B][COLOR=#000000]sudo shutdown -P 0 does not work.[/COLOR]
[COLOR=#000000] ieee80211 to me would suggest wireless drivers [/COLOR][/B][COLOR=#000000]
that is why I posted it in wireless section to begin with.[/COLOR]

---

### Post by jackofall1232 on 2013-04-06
ok I solved part of it.. The bcmwl kernel driver was corrupted so I uninstalled it and reinstalled it now I only have one more issue [COLOR=#000000][FONT=Ubuntu Mono][I] usb 1-1: >cleartt 1 (9032) error -19

[/I][/FONT][/COLOR]

---

### Post by jackofall1232 on 2013-04-06
ok marking solved. this is what I did. I purged B43 and then installed from software manager... bcmwl kernel  then that fixed the not shutting down issue but then I had no wifi. so I uninstalled bcmwl and installed B43 fwcutter and reboot ... Viola .. all good!

---

