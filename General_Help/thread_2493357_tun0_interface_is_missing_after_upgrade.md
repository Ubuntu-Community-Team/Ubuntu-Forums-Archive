---
title: "tun0 interface is missing after upgrade"
date: 2023-12-12
forum: General Help
---

### Post by gnikodym on 2023-12-12
Having a bad upgrade day...

First upgraded my macOS based RDP client (from Microsoft).  On restart, it could not connect to one of my Ubuntu boxen ([FONT=courier new]loki[/FONT]).  Of course, it is able to connect to a *different* Ubuntu box. Under duress, I rebooted the mac but alas did not change anything.  So I thought next I'll reboot [FONT=courier new]loki[/FONT]. While doing that, might as well do a quick [FONT=courier new]apt update; apt upgrade[/FONT] cycle.

When it came back, the RDB client still could not connect.  No worries, I'll just use the real keyboard.  First connect to work (pritunl client to a vpn).  Doesn't work?!?  New error message.  After much digging, I realized that [FONT=courier new]ifconfig[/FONT] no longer lists [FONT=courier new]tun0[/FONT] and none of the associated drivers are loaded.  wtf?

I can manually [FONT=courier new]modprobe ipip[/FONT] which gives me a [FONT=courier new]tun0[/FONT] but the vpn stuff still doesn't work...

Some questions:
1. what mechanism does the system use to decide what modules to load at boot? ie, what conf file needs the tunnel driver re-added
2. any other drivers a vpn client might need that might have gone missing?
3. any guesses about why RDP stopped working?
4. any other suggestions?

Thanks for anything

---

### Post by gnikodym on 2023-12-12
[partially SOLVED]

Turns out that re-importing my ovpn config into my client "fixes" the VPN issues.

The RDP problems are surely unrelated microsoft silliness.

Sorry for the bother.

---

### Post by MAFoElffen on 2023-12-12
No problem.

FYI...
```

mafoelffen@msi-ubuntu:~$ ls /etc/modprobe.d/
alsa-base.conf                  blacklist-framebuffer.conf   intel-microcode-blacklist.conf
amd64-microcode-blacklist.conf  blacklist-modem.conf         iwlwifi.conf
blacklist-ath_pci.conf          blacklist-oss.conf           mdadm.conf
blacklist.conf                  blacklist-rare-network.conf  nvidia-graphics-drivers-kms.conf
blacklist-firewire.conf         dkms.conf                    vfio.conf

mafoelffen@msi-ubuntu:~$ ls /etc/modules-load.d/
cups-filters.conf  modules.conf

```

---

