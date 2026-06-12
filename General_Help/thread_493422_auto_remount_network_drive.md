---
title: "auto remount network drive"
date: 2007-07-05
forum: General Help
---

### Post by zippercow on 2007-07-05
I have a network location (a partition on a Windows system) set to mount at boot, which works fine. The problem is my wireless network is not exactly stable, and the connection is often lost briefly. I can restore the connection using mount, but that's more than my wife wants to have to do. Does anyone know of a way to set a script or something to continuously try to mount a lost location until it comes back?

---

### Post by capitalistpiglet on 2007-07-05
just create the script to mount the drive and insert it into crontab, there is a gui for cron called kcron in kde and gnome-scheduler or gcrontab in gnome. just set it to run every 5 10 minutes.

---

