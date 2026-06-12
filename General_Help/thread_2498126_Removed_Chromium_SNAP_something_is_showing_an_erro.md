---
title: "Removed Chromium SNAP: something is showing an error on boot for something w/chromium"
date: 2024-05-31
forum: General Help
---

### Post by bmullan2 on 2024-05-31
Ubuntu 22.04 (all updated/upgraded)

I removed the Chromium SNAP after having it installed for a year.

> [B]$ sudo snap remove chromium --purge
[/B]

on *every reboot now *I get an error message:

> [B]
/var/lib/snapd/snaps/chromium_2713.snap: Can't open blockdev
[FAILED] Failed to mount Mount unit for chromium, revision 2719[/B]


I've tried to find what's causing this for 2 weeks with no success so thought I'd ask here.

---

### Post by VMC on 2024-05-31
what does 'snap list' show.

---

