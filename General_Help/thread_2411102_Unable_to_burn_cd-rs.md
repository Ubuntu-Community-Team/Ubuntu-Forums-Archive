---
title: "Unable to burn cd-rs"
date: 2019-01-24
forum: General Help
---

### Post by merlinus on 2019-01-24
Since re-installing 18.04.1, I cannot burn cds (or dvds).  I have set up my account to use cd-rom drives, and am a member of the root group.  This happens with both Brasero and K3b.  The error msg on K3b is to the effect that it does not have permission to burn discs.

The same thing happens on a different 18.04 computer as well.  I am the owner of the files I want to burn.  I tried to chown /dev/sr0 so that I am the owner, but that did not change anything.

---

### Post by merlinus on 2019-01-24
[FONT=Verdana]Here is the K3b error msg: 

[/FONT]cdrecord has no permission to open       the device.  The cd drive is selected in Settings.

I am also a member of the cdrom group.

---

### Post by merlinus on 2019-01-24
This command seems to have solved the issue:

sudo chmod 4711 /usr/bin/wodim; sudo chmod 4711 /usr/bin/cdrdao

---

