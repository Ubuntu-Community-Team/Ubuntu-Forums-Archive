---
title: "Raid Fubar"
date: 2008-02-15
forum: General Help
---

### Post by junk man on 2008-02-15
I installed Ubuntu 7.1 on a desktop with a ASUS A7n8XE motherboard & 2 250 gig Western Digital SATA drives.  I was playing around & decided to set up a Raid 1.  I should have researched first but figured I could reinstall & correct any problems since neither drive had any critical data.  The Raid utility didn't complete & now whenever I boot, the system doesn't recognize either drive & so goes to boot off the CD.  I get an error message "Raid 1 set in critical mode"  When I enter the raid utility, the keyboard doesn't work at all & I have to turn the power off.  I can boot with a live CD & read/write to either HD.  What can I do so that the drives will be recognized during the POST?  If I can get the drives recognized, I can start over.  This machine is for play & learning & so not critical.

---

### Post by Sudz on 2008-02-16
The drives may have been assigned to the raidcontroller by the BIOS but the RAID controller is unable to deal with them.  Try disabling the RAID controller and see if the drives show up.

---

