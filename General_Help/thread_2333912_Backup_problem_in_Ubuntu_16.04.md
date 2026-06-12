---
title: "Backup problem in Ubuntu 16.04"
date: 2016-08-14
forum: General Help
---

### Post by inextinguishable on 2016-08-14
I want backup for the my system. However a problem is occured. The my problem: 
"Could not back up the following files. Please make sure you are able to open them."
/home/kursat/.cache/dconf
/home/kursat/.dbus
/home/kursat/.local/share/recently-used.xbel
Can you help me?

---

### Post by mook765 on 2016-08-17
I think that this problem occurs due to permissions/ownership off the mentioned files/folders.
If you backup under your user-credentials you may not have any permissions on these files/folders, they may owned by root and only root can access them.
Please do _not_ change permissions or ownership off these files/folders.
Best way to backup is to run a backup-tool booted from CD or USB, so the system you want to backup is not running.
To get an overview about backup in Ubuntu please refer to this link:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

