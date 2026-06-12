---
title: "Administration menu error"
date: 2006-11-11
forum: General Help
---

### Post by likwidoxigen on 2006-11-11
The configuration could not be loaded.
You are not allowed to access the system configuration.


I recently nerfed my group file however I did revert it back to the state it was in and now it's fine however I still cannot access the administration menu when it doesn't run as root. For example I can still get into Synaptic but not networking. Any ideas?

---

### Post by fragos on 2006-11-12
Check the following substituting your hostname for Geo which is mine.

If you can't run administrative applications, check:

/etc/hostname must be "Geo"
/etc/hosts must start with "127.0.0.1 localhost Geo"

These files must be in agreement or admin can't be performed.

---

### Post by Fabiano Shark on 2006-11-15
> **likwidoxigen said:**
> The configuration could not be loaded.
You are not allowed to access the system configuration.


I recently nerfed my group file however I did revert it back to the state it was in and now it's fine however I still cannot access the administration menu when it doesn't run as root. For example I can still get into Synaptic but not networking. Any ideas?

If you installed in OEM mode, run **sudo oem-config-prepare** to clean up the temporary files, so reboot the system and run **gksu users-admin** and give the all privileges you want to your user. ;)

---

