---
title: "Major bug in detecting a wired router"
date: 2012-12-06
forum: General Help
---

### Post by skippy_dude on 2012-12-06
I'll submit a proper bug report in a while, but I noticed that if my kubuntu (the latest LTS version) machine does this.
Steps to reproduce.
Setup:
1. Have a kubuntu 64 bit installation.
2. A connection to a router via LAN cable.

Steps:
1. Turn off the machine and the router.
2. Turn on the machine and wait till booted completely, log in and have the machine idling on the desktop.
3. Turn on the router.

Notice:
The router never connects.

This only happens if the router was plugged in to the computer and turned off. It doesn't happen if it was already on or not connected at all during boot.
Nothing is wrong with the router as I can reproduce the bug at will following those steps. It is with that very router that I am online right now.

---

### Post by Ms. Daisy on 2012-12-08
That's not a bug. That's the way routers work.

You need to bring up the devices in a particular order so that DHCP works. If you bring up the computer before the router then the computer will assign itself a non-routable IP address because the router isn't up to give it an IP.

1. turn everything off
2. bring up the modem. Wait until it's fully up.
3. bring up the router. Wait until it's fully up.
4. turn on the computer. Voila! You have a routable IP.

---

### Post by colin.p on 2012-12-08
Certainly not as a slight on the OP, but after 4 years working the phones for Road Runner Business Class, if I had a dollar for everytime I had the caller go through that routine.........(sigh)

---

