---
title: "CUPSys Problems"
date: 2006-07-16
forum: General Help
---

### Post by bluecherry on 2006-07-16
Hi all,

I'm having trouble installing my Epson AcuLaser C1100 laser printer on Dapper.

The non-free epson driver that is required for this printer worked fine on Breezy. I barely ever print so I didn't bother to install the driver up until now :o.

Situation: Epson AcuLaser C1100 connected to WinXP in other room, Ubuntu connects over LAN (SMB).

On Breezy I did:
Download source from epson.
./configure, make, sudo make install
Restart cupsys
System>Admin>Printers>Add printer and it worked just like that.

This is what I did on dapper:
1. Tried Breezy solution
2. Downloaded the RedHat/Suse rpm from Epson, alien -d, dpkg -i
3. Tried a suggested fix (from somewhere on this forum) where you copy the cups config files from the Mephis distro. No success. Completely removed cupsys and relevant packages + reinstall.
4. Somebody posted that his problem was solved by rebooting windows, did that, no luck.

What's wrong:
* printer shows "Pauzed" in System>Admin>Printers
* In printer jobs status says: "On hold: printer-stopped"
* I'm getting 2 drivers when I select the printer instead of one (name = but still 2 listing, beheavior seems the same?)
* sometimes the "data" LED on the printer lights up when I try to print but it seems to be random (haven't been able to reproduce this beheavior)..

Any ideas?

Thx!

---

