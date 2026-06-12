---
title: "Palm Tungsten T5 don't sync with kontact/kpilot"
date: 2007-05-30
forum: General Help
---

### Post by clauguia on 2007-05-30
My Palm Tungsten T5 syncs with pilot-link command line, No problem, so I don't think is visor, usb, kernel and such. But I can't use all those pdb files in a sensible way. I wish I could sync it with kde apps such as kontact, but I'm not shure if I can use kontact directly with pilot-link.

Kpilot just doesn't work. I can sometimes get through the wizard, and then comes out an /dev/ttyUSB3 port, but system message says the palm is connected to the /dev/ttyUSB0 and /dev/ttyUSB1. pilot-link works with no -p argument after i do the following command, once after a reboot: 

$ export PILOTPORT=/dev/ttyUSB1

(Oh, thats another question, can I put that command line somewere so that I don't need to do it everytime sistem restarts?)

I've tryed hotsync first, kpilot after and the opposit too. it simply doesn't listen.

i use kubuntu dapper.
pilot-link version 0.11.8
Qt: 3.3.6
KDE: 3.5.2
KPilot: 4.6.0 (blivit)

/var/log/syslog---------------------------------------------------------
(...)
May 30 18:36:56 kunhantan-desktop kernel: [17185954.884000] usb 1-2: new full speed USB device using ohci_hcd and address 33
May 30 18:36:56 kunhantan-desktop kernel: [17185955.104000] visor 1-2:1.0: Handspring Visor / Palm OS converter detected
May 30 18:36:56 kunhantan-desktop kernel: [17185955.104000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
May 30 18:36:56 kunhantan-desktop kernel: [17185955.104000] usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
May 30 18:37:02 kunhantan-desktop kernel: [17185960.880000] usb 1-2: USB disconnect, address 33
May 30 18:37:02 kunhantan-desktop kernel: [17185960.880000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
May 30 18:37:02 kunhantan-desktop kernel: [17185960.880000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
(...)
---------------------------------------------------------------------------------

---

### Post by clauguia on 2007-06-01
Well,

I found in KDE 3.5.7 Changelog ([http://www.kde.org/announcements/changelogs/changelog3_5_6to3_5_7.php]("http://www.kde.org/announcements/changelogs/changelog3_5_6to3_5_7.php")) the following info about kpilot:

> KPilot
Improvements:

    * Cleanups in memofile conduit; using new OS5 database if it's present, otherwise falling back to legacy one. See SVN commit 654396. 

So, I installed Kubuntu Feisty (ok, now I will have to rebuild all my things again, maybe its possible to run KDE 3.5.7 in Ubuntu Dapper, but I was afraid), and followed Kubuntu howto to install KDE 3.5.7 ([http://kubuntu.org/announcements/kde-357.php]("http://kubuntu.org/announcements/kde-357.php")).

After that, i installed kdepim package from Adept (and not only kpilot form Add/Remove programs). Than I installed pilot-link via apt-get ($ sudo apt-get install pilot-link) and than followed the instructions of pilot-link README ([http://www.pilot-link.org/README.usb]("http://www.pilot-link.org/README.usb")) being, on short, the following (this are just for knowllege, if you want to do it, refer to the README instead):

> # /sbin/modprobe uhci_hcd
# /sbin/modprobe usbserial
# /sbin/modprobe visor
# /bin/mknod /dev/ttyUSB0 c 188 0
# /bin/mknod /dev/ttyUSB1 c 188 1
# /bin/chmod 0666 /dev/ttyUSB0
# /bin/chmod 0666 /dev/ttyUSB1
Create a file /etc/udev/rules.d/pilot.rules, with the following information in it (all on one line, and do not make a typo or it will not work properly): BUS=="usb", SYSFS{product}=="Palm Handheld*|Handspring *", KERNEL=="ttyUSB*", NAME="ttyUSB%n", SYMLINK="pilot", GROUP="usb", MODE="0666"
$ sudo /etc/init.d/udev restart
Edit /etc/environment adding the line: export PILOTPORT=/dev/ttyUSB1

After that, pilot-link worked again (as it was working with Dapper).
So, I opened up my Kpilot, followed the wizard (i just didn't probe for port and user, I let /dev/pilot and, as for my username, it shows on up right in the HotSync screen). I chose KDE suite.

And, time of truth, I hit HotSync. It did sync! Every db! Nice... But wait! I oppened KOrganizer and no events. I looked in Kpilot - todo viewer - nothing. In Generic DB Viewer, CalendarDB-PDat.pdb, CalendarLocationsDB-PDat.pdb and DatebookDB.pdb are there. But I cant still use them in the KDE KOrganizer. Err, is something missing yet?

---

### Post by clauguia on 2007-06-02
I found out that only future appointments appear on Kontact. I was expecting past calendar notes to apear as well. So, its working, though I'll have to look on this past/future thing because I take notes of events and want them to appear there too.

It also seams that I have to open Kpilot while hotsync is running, and I can't leave deamon running or it will not hotsync anymore.

Also, when I close kpilot daemon after a hotsync it crashes with an error. I'll try to get in touch with kde community, I am not familiar with bug reports, though.

So, it seams its minor things to solve now. The important parts are running.

---

