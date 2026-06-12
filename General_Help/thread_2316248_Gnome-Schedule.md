---
title: "Gnome-Schedule"
date: 2016-03-06
forum: General Help
---

### Post by will97 on 2016-03-06
I am using GNOME-SCHEDULE GUI to try and automate backing up my desktop files to google drive via the grive command upon reboot of my computer (ie as soon as my computer is started, I want the grive command to run automatically. whether turning on the computer or restarting it). It does not seem to be working. I know I'm typing in the command into the GNOME-SCHEDULE correctly, because when I set the automated grive command to run every minute, it works. Any suggestions on what to do?

---

### Post by TheFu on 2016-03-10
I don't know anything about google-drive (don't use google stuff here) or gnome-schedule, but if there is a GUI it won't work until the userid logs in.

Perhaps using a tiny script and standard cron would work?  Just be certain to specify the full path to all programs called inside the script AND set the PWD to where you need to be - cron doesn't set a full environment or the CWD.

But > Grive can be considered still beta quality.  [https://github.com/Grive/grive](https://github.com/Grive/grive) - BTW, it doesn't say **anything** about uploading files at all. It says it will download files (not all of them) from google-drive to the PWD.  Is this the same tool?

---

