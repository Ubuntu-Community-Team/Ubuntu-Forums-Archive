---
title: "Strange behavior on upgrade"
date: 2005-04-01
forum: General Help
---

### Post by holomorph on 2005-04-01
I've got a costom xorg.conf (really just added the "NoDDC" option to the "Device" section for my nvidia card).  I'm not sure if it happens every time, but often, after I download and insall upgrades, the next time I boot the X server fails to start (something about No Screens Found).  The way I have discovered to fix this is 'sudo dpkg-reconfigure xserver-xorg' and then re-adding the "NoDDC" line.  Then X will start up fine.  The funny thing is, the new xorg file and the old one are identical!  I can even reconfigure and then copy the backup of the old file right over the new one and X starts fine.  I find this very strange.  Has anyone got any ideas what is happening here?

---

