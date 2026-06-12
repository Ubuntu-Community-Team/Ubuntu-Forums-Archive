---
title: "Ubuntu 18.04 - Complete Hard Freeze"
date: 2018-07-26
forum: General Help
---

### Post by curse4444 on 2018-07-26
Hi Folks,

I'm new to these forums and I'm moderately new to the Linux desktop scene. My desktop is hard freezing and I don't know what the problem is. During use the entire screen will freeze and I have to hard reset the box. I don't really know what logs to look at but /var/log/syslog shows the following during a freeze:

```
Jul 26 19:09:40 ElephantBox snapd[1239]: snap "gnome-system-monitor": snap has no updates available
Jul 26 19:09:40 ElephantBox snapd[1239]: 2018/07/26 19:09:40.063736 autorefresh.go:387: auto-refresh: all snaps are up-to-date
Jul 26 19:10:09 ElephantBox org.gnome.Shell.desktop[2126]: (/usr/lib/firefox/firefox:5767): dconf-WARNING **: 19:10:09.170: Unable to open /var/lib/snapd/desktop/dconf/profile/user: Permission denied
Jul 26 19:12:30 ElephantBox systemd[1]: Started Session 4 of user peter.
[B]Jul 26 19:12:50 ElephantBox systemd[1]: Started Session 5 of user peter.
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@[/B]Jul 26 19:15:55 ElephantBox systemd-modules-load[474]: Inserted module 'lp'
Jul 26 19:15:55 ElephantBox systemd-modules-load[474]: Inserted module 'ppdev'
```

Here are some details about my system:
peter@ElephantBox:/var/log$ uname -a
Linux ElephantBox 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Hardware:
AMD Ryzen 1700
Asus Crosshair VI Motherboard
AMD R9 Fury X
AMD RX 480
Samsung 500 GB SSD
4 SATA Drives in a software raid 5
32 GB of 2400 Mhz RAM

I'm running the latest AMD graphic drivers (radeon pro drivers). Additionally, I performed a dist-upgrade after initial install, then added the padoka-ppa and performed another upgrade to get the bleeding edge mesa graphics. I also grabbed the latest source code from Cosmic for x11vnc and compiled that and manually threw it into /usr/lib/ and /usr/bin (x11vnc_0.9.13-6 packaged with 18.04 has this annoying system crash bug that isn't fixed until a later version). x11vnc is currently running as a service via systemd so I can remotely login at startup. This computer is mostly used as a headless box for fun things like hosting game servers / vms / casual linux gaming / hobbyist development.

Edit: I forgot to mention that I installed lightdm and made that default over gdm for use with x11vnc.

---

### Post by curse4444 on 2018-07-27
I think I have this figured out just from tinkering alone. The two video cards did not play nice together. I ended up removing the R9 Fury X and decided to just use the RX 480. (The RX 480 is outperforming the R9 Fury according to my own independent benchmarks in games that I tested (Rise of the Tomb Raider & Dying Light)). Additionally, I ditched x11vnc_0.9.13-6 and compiled 0.9.15 from source since the earlier version still had some stack smashing errors. So far no hard freeze has occurred and the computer is much snappier through use via Steam Streaming client and x11vnc. I'll update here if any additional freezing is experienced.

---

