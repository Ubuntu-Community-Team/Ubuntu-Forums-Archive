---
title: "Enable Wireless Via Command Prompt? Help!"
date: 2007-08-24
forum: General Help
---

### Post by GSF1200S on 2007-08-24
Ok, so I finally wiped Kubuntu and decided to install the Ubuntu kernel. My plan was to install KDE core, as Kubuntu is a little slow and has given me, at least, some annoying issues. Despite distro hopping (pclos, opensuse, etc), I really like the ubuntu kernel, apt, synaptic, and kde.

Everything went fine throughout the install, but Ive got an issue. How do I setup my wireless connection from the command prompt? I had planned on using a hard line, but letting it try and connect via dhcp brings me no luck. It doesnt seem to work with linux, not that I care (hasnt worked with any distro).

i would assume the command line install still uses the restricted modules, and during the install process it seemed that was the case. My wireless card (Atheros) needs the restricted modules to work. I remember during the install process it asking to setup my primary connection. After an autoconfig failed, I did some looking around and managed to get it connected via using my routers essid (it said it worked, no wep or wpa). Problem is, when I booted the system, I had no internet connection. Attempts to apt-get update and install kde core were unsuccessful.

Question is, how do I get ath0 (wireless) setup from the command prompt? Im assuming Id need the command to enable the network connection, and then another to connect to the ESSID that I want. At least ESSID would be the easiest way. Anyway I can get a net connection so I can get KDE core going would be awesome. Im on windows right now.. I dont know how much longer I can take it!! :)

---

### Post by InGunsWeTrust on 2007-08-25
If at all possible it would be much easier to do something like that from a wired connection. But all network interfaces are configured with

```
ifup eth0
```

eth0 being an example of an interface. To get a list of interfaces to choose from do

```
ifconfig
```

---

