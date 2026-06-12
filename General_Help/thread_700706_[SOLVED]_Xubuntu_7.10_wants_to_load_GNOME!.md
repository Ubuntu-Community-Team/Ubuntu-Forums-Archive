---
title: "[SOLVED] Xubuntu 7.10 wants to load GNOME!"
date: 2008-02-18
forum: General Help
---

### Post by Bruce M. on 2008-02-18
Xubuntu 7.10 wants to load GNOME for some reason!

My machine:
P-III - 800Mhtz - 512MB RAM
Motherboard: Intel D815EEA - sound and video built in.
sda1 = W2K
sda5 = /root
sda7 = /home
sdb1 = my personal drive

Here's what I did:

Three days ago I did a clean install of Ubuntu 7.10 over 7.06
- /root - reformated
- /home - kept the data

It was slower than Feisty, running 186 processes vs 94 and using 18% CPU sitting idle vs 4%.  Also I couldn't get Conky to run at startup, althought it ran fine from terminal ( ./.startconky )

So today I installed Xubuntu. Conky tells me it's running 96 processes running idle the CPU is at 11%.

But the Update manager tells me it wants to install:

gnome-cards-data
gnome-games
gnome-games-data
gnome-system-monitor
gnome-system-tools
gtk2-engines

Would this be because I preserved my home folder and that there is something in there that requires GNOME (like game scores, etc)

Also: it loaded the complete "OpenOffice" package.

Should I reinstall Xubuntu complete with a new /home partition as well?
I have everything backed up and personal stuff saved to my data drive (sdb1)

**EDIT:** 21 Feb 2008: Forget this, I went back to Ubuntu and turned Compiz off.

---

