---
title: "Slow Startup - Text Startup?"
date: 2007-06-12
forum: General Help
---

### Post by ExxonValdeez on 2007-06-12
My computer has recently experiencing very slow startup times. Is there a key command that I can press to get a text startup so I can see what is causing the problem? Also, any other suggestions? If hardware specs are needed I can provide them. Thanks!

---

### Post by reclusivemonkey on 2007-06-13
> **ExxonValdeez said:**
> My computer has recently experiencing very slow startup times. Is there a key command that I can press to get a text startup so I can see what is causing the problem? Also, any other suggestions? If hardware specs are needed I can provide them. Thanks!

You can use dmesg after boot to have a look what was going on, pipe it through more or less to read a page at a time. Installing bootchart will give you a pretty graph of what's going on during the boot process.

---

### Post by ExxonValdeez on 2007-06-13
Bootchart worked well. Now I just need to diagnose the chart. It seems that i have some KDE servies running because I installed the kubuntu desktop package. Is there a way to remove some of these components or stop them from starting? I looked in the Bootup Manager program but I didn't see any of these services. Mainly the "k" ones starting at the beginning of the process. [http://web.omnidrive.com/APIServer/shared/ncQkHPuJk4r0pCbda1PHoqTc/feisty-20070613-1.png]("http://web.omnidrive.com/APIServer/shared/ncQkHPuJk4r0pCbda1PHoqTc/feisty-20070613-1.png")

---

### Post by ExxonValdeez on 2007-06-15
Well, it looks like its the wifi drivers having a problem with the WEP or something.This is the end of dmesg:

```
[   97.488000] Bluetooth: HCI socket layer initialized
[   97.552000] Bluetooth: L2CAP ver 2.8
[   97.552000] Bluetooth: L2CAP socket layer initialized
[   97.716000] Bluetooth: RFCOMM socket layer initialized
[   97.716000] Bluetooth: RFCOMM TTY layer initialized
[   97.716000] Bluetooth: RFCOMM ver 1.8
[  294.964000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  310.804000] ieee80211_crypt: registered algorithm 'WEP'
[  310.932000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  328.304000] eth1: no IPv6 routers 
```

I guess I could do a reinstall but I don't think that would help much. Any suggestions?

---

