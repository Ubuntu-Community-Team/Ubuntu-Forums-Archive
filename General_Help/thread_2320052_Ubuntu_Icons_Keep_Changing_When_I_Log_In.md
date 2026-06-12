---
title: "Ubuntu Icons Keep Changing When I Log In"
date: 2016-04-09
forum: General Help
---

### Post by jonathan90 on 2016-04-09
Hi, I rebooted my computer after installing updates from Update Manager, and my icons keep changing to a icon set I didn't choose, and I can't change it, but after I reboot, it'll let me do it before reverting back to this icon set. I made a custom set a few months ago and kept using it without problems until now. Anyone know what's going on? Thanks!!!

EDIT: After about 10 reboots it seems to be working, but I'm not sure if the issue will go away. Here is the output of .xsession-errors and xsession-errors.old

.xsession-errors

Script for ibus started at run_im.
init: indicator-bluetooth main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth respawning too fast, stopped

.xsession-errors-old

Script for ibus started at run_im.
init: unity-settings-daemon main process ended, respawning
init: hud main process (2107) terminated with status 1
init: gnome-session (Unity) main process (2112) terminated with status 1
init: indicator-printers main process (2213) terminated with status 1
init: logrotate main process (1999) killed by TERM signal
init: mediascanner-2.0 main process (2016) terminated with status 99
init: unity-panel-service main process (2127) terminated with status 1
init: indicator-bluetooth main process (2201) killed by TERM signal
init: indicator-power main process (2203) killed by TERM signal
init: indicator-datetime main process (2208) killed by TERM signal
init: indicator-session main process (2229) killed by TERM signal
init: indicator-application main process (2260) killed by TERM signal
init: unity-settings-daemon main process (2547) killed by TERM signal
init: Disconnected from notified D-Bus bus

What my desktop normally looks like
[http://i.imgur.com/vebCSjI.png](http://i.imgur.com/vebCSjI.png)

Screenshot of my desktop now
[URL="http://i.imgur.com/RyQzyMR.png"]http://i.imgur.com/RyQzyMR.png
[/URL]

My custom icon set

[Icon Theme]
Name=Moka+Ubuntu-mono-light+Vibrancy-Nonmono-Light-Orange
Comment=A merge of Moka, Ubuntu Mono Light, and Vibrancy Orange
Inherits=my-ubuntu-mono-light,my-moka,orig-vibrancy-nonmono-light-orange
# KDE Specifics

DisplayDepth=32

LinkOverlay=link
LockOverlay=lockoverlay
ShareOverlay=share
ZipOverlay=zip

---

