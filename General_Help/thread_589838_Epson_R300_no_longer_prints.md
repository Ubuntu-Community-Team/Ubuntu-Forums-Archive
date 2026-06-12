---
title: "Epson R300 no longer prints"
date: 2007-10-24
forum: General Help
---

### Post by Wingcommander on 2007-10-24
Hi all,
just upgraded to Gutsy and my printer no longer prints. Any jobs sent to it are listed as "stopped" with no option to "start" them.

I've tried the "sudo aa-complain cupsd" as recommended in other threads but it doesn't seem to do anything.

Please let me know what info you'd like me to post whilst helping me with this.

Thanks in advance...

---

### Post by Wingcommander on 2007-10-24
Ok, here's some more info ...

I typed :
**/tmp$ tail -f /var/log/cups/error_log**

and got ...

E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: If the previous installed version of Gutenprint
E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: was 4.3.19 or higher, you can use the `cups-genppdupdate.5.1'
E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: program to do this; if the previous installed version
E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: was older, you can use the Modify Printer command via
E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: the CUPS web interface: [http://localhost:631/printers](http://localhost:631/printers).
E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: The version of Gutenprint software installed (5.1.3) does not match the PPD file (5.0.1).
E [24/Oct/2007:16:00:06 +0000] PID 16283 (/usr/lib/cups/filter/rastertogutenprint.5.0) stopped with status 1!
E [24/Oct/2007:16:00:07 +0000] [Job 75] Job stopped due to filter errors.
E [24/Oct/2007:16:12:23 +0000] Pause-Printer: Unauthorized
E [24/Oct/2007:16:12:27 +0000] Resume-Printer: Unauthorized

Should I try and retro my gutenprint to 5.0.1 or upgrade my PPD file to 5.1.3?
Either way, any help would be useful. Google results just keep on telling me to do the same thing - sudo aa-complain cupsd - which doesn't work.

Thansk,

---

### Post by lopzided on 2007-10-26
I'm having the same problem with my Epson Stylus CX5000 printer.  Worked fine before the Gutsy upgrade.

Also, interestingly, in my System/Administration menu, there are now TWO items listed as Printing.  One of them opens the window titled Printer Configuration - localhost, and the other opens the Printers dialog (showing the icons for New Printer, as well as TWO instances of my printer).

I have tried removing the printers and adding a new one.  Still no printing.

I tried the sudo aa-complain cupsd trick as well.  No dice.

Help!

EDIT: my output from tail -f /var/log/cups/error_log:

slop@slopbuntu:~$ tail -f /var/log/cups/error_log
E [26/Oct/2007:15:41:48 +0000] CUPS-Delete-Printer: Unauthorized
E [26/Oct/2007:15:42:25 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [26/Oct/2007:15:42:25 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [26/Oct/2007:15:42:50 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [26/Oct/2007:15:44:39 +0000] CUPS-Set-Default: Unauthorized
E [26/Oct/2007:15:45:34 +0000] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [26/Oct/2007:15:45:34 +0000] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [26/Oct/2007:15:45:40 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [26/Oct/2007:21:39:41 +0000] Pause-Printer: Unauthorized
E [26/Oct/2007:21:39:42 +0000] Resume-Printer: Unauthorized

---

### Post by d_e_monat on 2007-11-04
I, too, am having this problem.

After upgrade to Gutsy, I had two Printing menu items under System>Administration.  I also had two "pop-up" printer icons on the top panel.

My Epson 880 stopped working.  I deleted it and could not reinstall it because it was not recognised on the LPT port.  :(

I read about the sudo aa-complain cupsd trick and after trying that the printer was recognised on the LPT port.  Then I reinstalled it.

I removed the gnome-cups-manager package and one of the Printing menu items went away.  Unfortunately the "pop-up" icons were gone, too.

All through this I have not been able to print a single test page (or anything else).

I reinstalled the gnome-cups-manager and the two "pop-up" icons came back.  Seems I have none or two!!!

Can anyone help???

It seems that the LPT port is not comunicating with the printer.  Yes I checked the plug  :)

---

