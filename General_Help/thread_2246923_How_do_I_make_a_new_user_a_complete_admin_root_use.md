---
title: "How do I make a new user a complete admin root user?"
date: 2014-10-04
forum: General Help
---

### Post by dorlow on 2014-10-04
Ok, I was having some weird problems with my computer and I couldn't figure out how to fix them.  But then I discovered that a new user all the problems went away.  I created the user and added them to the root group which makes the user part of group 0.  But when I login as the user, I go into the system settings and most of the settings are missing.  I only can administer printers and updates.  So, obviously I'm still not a complete admin on the machine yet.

---

### Post by dorlow on 2014-10-04
Well, beats me how it's fixed but it somehow fixed itself.  All my options are there now.

---

### Post by sotiris2 on 2014-10-04
Actually I don't think you should be part of the root group. Running ```
groups
``` on my admin user in a week old installation yields ```
sotiris adm cdrom sudo dip plugdev lpadmin sambashare
``` Notice how there is no root group there.  [Apparently]("http://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu") each group allows for ```
adm         Monitor system logs
cdrom       Use CD-ROM drives
lpadmin     Configure printers
sudo        administer the system, ...
sambashare  Share files with the local network
dip         Connect to the Internet using a modem
plugdev     Access external storage devices
```

I would add those and remove root group.

---

### Post by TheFu on 2014-10-04
The adm and sudo groups are the key most of the time. There are exceptions, sometimes, but on recent Ubuntu, that should be it.  The other groups happen when logged into the console ... oh - sambashare - that's a new one for me.

On my samba sharing system, I am not a member. Perhaps using the GUI to share does that?  I don't GUI much an never have with samba stuff.

---

### Post by sotiris2 on 2014-10-04
Actually I also haven't configured samba at all on this system, infact it is not even installed, but it appears ubuntu's first user is added to sambashare anyway..

---

