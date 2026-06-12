---
title: "kde-systemsettings crashing"
date: 2008-01-13
forum: General Help
---

### Post by maestrobwh1 on 2008-01-13
System settings is crashing for some odd reason.  I tried a purge and reinstall.  If I open terminal and do it from there, I don't get much more information, but if I run it as sudo (kdesu), it opens.

I did have a minor issue with kcontrol also, but it flashed up a message that I could not write to .kde/share/config/kcontrolrc so I just changed the user to myself as the user.  It somehow got marked as root.

I now can launch kcontrol, but not systemsettings as a normal user.  

$ systemsettings
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
KCrash: Application 'systemsettings' crashing...

---

