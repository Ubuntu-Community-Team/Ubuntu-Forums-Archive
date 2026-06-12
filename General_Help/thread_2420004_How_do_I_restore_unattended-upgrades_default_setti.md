---
title: "How do I restore unattended-upgrades default settings and conf files?"
date: 2019-05-28
forum: General Help
---

### Post by jdrch on 2019-05-28
Anyone know how to do the above in 19.04? Thanks!

---

### Post by Tadaen_Sylvermane on 2019-05-28
I'd think the easiest way would be to purge and reinstall.

```
sudo apt --purge autoremove unattended-upgrades && sudo apt install -y unattended-upgrades
```

One thing I've gotten in the habit of doing. If I'm messing about with configuration files in /etc/ I first copy the original default file to a backup, say like so.

```
sudo cp /etc/snapraid.conf /etc/snapraid.conf.bak
```

That should always keep an original config file available for reference.

---

### Post by deadflowr on 2019-05-28
The system default settings are in /usr/share/unattended-upgrades/
Will have both the 50unattended-upgrades and the 20auto-upgrades files with the system defaults.
Copying both files over to the /etc/apt/apt.conf.d directory will reset it to the defaults.

---

