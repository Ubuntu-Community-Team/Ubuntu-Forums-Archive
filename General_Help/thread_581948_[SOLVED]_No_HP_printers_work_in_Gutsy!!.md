---
title: "[SOLVED] No HP printers work in Gutsy!!"
date: 2007-10-19
forum: General Help
---

### Post by FuturePilot on 2007-10-19
None of my printers work in Gutsy. They worked fine in Feisty. I plug one in and it's detected but when I go to print a test page, nothing happens. I can't print anything from any other program either.
This is from my cups error log if it helps any.
E [19/Oct/2007:16:14:43 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [19/Oct/2007:16:14:54 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [19/Oct/2007:16:15:07 -0400] [Job 1] No %%BoundingBox: comment in header!
E [19/Oct/2007:16:15:43 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [19/Oct/2007:16:16:16 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [19/Oct/2007:16:16:22 -0400] [Job 2] No %%BoundingBox: comment in header!
E [19/Oct/2007:16:17:26 -0400] [Job 3] No %%BoundingBox: comment in header!
E [19/Oct/2007:16:17:45 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [19/Oct/2007:16:17:51 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [19/Oct/2007:16:17:56 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [19/Oct/2007:16:17:56 -0400] PID 15057 (/usr/lib/cups/backend/hp) crashed on signal 9!
E [19/Oct/2007:16:17:56 -0400] [Job 3] No %%BoundingBox: comment in header!
E [19/Oct/2007:16:17:56 -0400] PID 15056 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [19/Oct/2007:16:18:12 -0400] [Job 4] No %%BoundingBox: comment in header!
E [19/Oct/2007:16:30:45 -0400] CUPS-Delete-Printer: Unauthorized
E [19/Oct/2007:16:30:48 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [19/Oct/2007:16:31:28 -0400] [Job 6] No %%BoundingBox: comment in header!
E [19/Oct/2007:16:40:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [19/Oct/2007:16:40:03 -0400] CUPS-Delete-Printer: Unauthorized
E [19/Oct/2007:16:40:06 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [19/Oct/2007:16:40:26 -0400] [Job 7] No %%BoundingBox: comment in header!
E [19/Oct/2007:16:41:33 -0400] cupsdAuthorize: Local authentication certificate not found!
E [19/Oct/2007:16:41:33 -0400] CUPS-Delete-Printer: Unauthorized
E [19/Oct/2007:16:41:36 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [19/Oct/2007:16:42:00 -0400] [Job 8] No %%BoundingBox: comment in header!

---

### Post by caldevil on 2007-10-19
see this:

[http://www.dslreports.com/forum/r19213900-Printing-issues](http://www.dslreports.com/forum/r19213900-Printing-issues)

---

### Post by FuturePilot on 2007-10-19
Well, 2 out of my 3 printers automagically started working.:confused:
But 1 still won't work. It's an HP Color Laserjet 2550. It's detected but nothing prints. This is what I see in the cups error log
E [19/Oct/2007:17:32:44 -0400] [Job 18] No %%BoundingBox: comment in header!
:confused:

And why does it keep looking for ppds in /opt/share/ppd 
There's nothing in /opt!

---

### Post by FuturePilot on 2007-10-19
Got it working. Had to install cups-gnome-manager and install the printer through that.:confused::guitar:

---

### Post by drs305 on 2007-10-20
Deleted and posted in new thread.

---

