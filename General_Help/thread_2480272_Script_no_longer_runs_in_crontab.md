---
title: "Script no longer runs in crontab"
date: 2022-10-24
forum: General Help
---

### Post by AlexHudghton on 2022-10-24
I have a script in my crontab that runs @reboot to change the screen background to 'the one for today'

On upgrade to 22.04.1 the script no longer works from any crontab.

Running as a script from the desktop is fine.


#!/bin/bash

cd /home/alex/Wallpapers

DAY=`date +%j`

TYPE=".jpg"

BKG=$DAY$TYPE

cp $BKG /home/alex/Pictures/Wallpapers/Wallpaper

/usr/bin/gsettings set org.gnome.desktop.background picture-uri-dark "file:///home/alex/Pictures/Wallpapers/Wallpaper"

---

### Post by TheFu on 2022-10-24
No script that interacts with the GUI should be run using 'cron' or 'at' or 'batch'.  These are non-GUI tools.
If you want to change the background.
a) a user must be logged in and have either a Wayland and X11 "session".  That doesn't happen BEFORE the user logs in on the machine and the GUI under their user is run.
b) Use the 'autostart' feature of your DE or Window Manager to run anything at login for a user GUI session.  Every DE has a Desktop Guide which explains how to accomplish this.

Suppose the system reboots (for any reason) and the user isn't anywhere near it. No user logs into the system for 4+ hours, so no "Session" exists.  Every GUI command will fail, just wasting resources.  This is why we don't use systemd with automatic restart for per-user GUI stuff either.

[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en) is from the Ubuntu Desktop Guide for the Gnome DE.

I don't use gnome, but setting the background on X11 has always been easy using 'feh'.  I doubt it will work for Wayland.
```
feh --bg-max "/full/path/to/image.png"
```
But xsetroot and probably 100 other programs can be used, at least for X11.

---

