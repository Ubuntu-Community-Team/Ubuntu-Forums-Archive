---
title: "HP LaserJet 4250 can be seen but does not print"
date: 2008-01-10
forum: General Help
---

### Post by westwinger on 2008-01-10
I'm sorry to bring up the same problem as many other threads but my printer is recognized but does not print.  It is an HP LJ 4250 connected directly to my ubuntu box by usb.

I went to localhost:631/printers where I found:

hp_LaserJet_4250 (Default Printer) "printmode mismatch with pen, tray, etc."
Description: Hewlett-Packard hp LaserJet 4250
Location:
Printer Driver: HP LaserJet 4250 Foomatic/hpijs
Printer State: processing, accepting jobs, published.
Device URI: hp:/usb/hp_LaserJet_4250?serial=CNBXC25740

I then went to the Printer Configuration GUI and played around with the Printout Mode (changed "Controlled by Printout Mode" to "300 dpi, Greyscale, etc") and changed the trays but nothing happened. I have 4 test pages in the queue.

I'm trying to switch 20 users from XP to Ubuntu but that's a non-starter if I can't print.  Please help.

---

### Post by stchman on 2008-01-10
> **westwinger said:**
> I'm sorry to bring up the same problem as many other threads but my printer is recognized but does not print.  It is an HP LJ 4250 connected directly to my ubuntu box by usb.

I went to localhost:631/printers where I found:

hp_LaserJet_4250 (Default Printer) "printmode mismatch with pen, tray, etc."
Description: Hewlett-Packard hp LaserJet 4250
Location:
Printer Driver: HP LaserJet 4250 Foomatic/hpijs
Printer State: processing, accepting jobs, published.
Device URI: hp:/usb/hp_LaserJet_4250?serial=CNBXC25740

I then went to the Printer Configuration GUI and played around with the Printout Mode (changed "Controlled by Printout Mode" to "300 dpi, Greyscale, etc") and changed the trays but nothing happened. I have 4 test pages in the queue.

I'm trying to switch 20 users from XP to Ubuntu but that's a non-starter if I can't print.  Please help.

That printer works perfectly using the Postscript driver.  When you go to the web based CUPS change everything from A4 to Letter.  Since Ubuntu is written overseas they use A4 while poeple in the US use Letter.

---

### Post by westwinger on 2008-01-10
Changed to postscript and checked the tray (letter).  Still nothing.
Any ideas?

---

### Post by westwinger on 2008-01-10
Perhaps I should add that mine is a dual boot system with XP and the printer works fine under XP.

---

### Post by westwinger on 2008-01-10
Please help!

At CUPS 1.3.2 browser I'm getting this error message:
"open print channel failed; will retry in 30 seconds..."

This is my error log:
E [10/Jan/2008:17:02:31 -0500] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2008:17:02:35 -0500] cupsdAuthorize: Local authentication certificate not found!
E [10/Jan/2008:17:02:35 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [10/Jan/2008:17:02:35 -0500] PID 9286 (/usr/lib/cups/backend/hp) crashed on signal 9!
E [10/Jan/2008:17:02:37 -0500] PID 9285 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2008:19:11:42 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [10/Jan/2008:19:12:33 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [10/Jan/2008:19:12:35 -0500] PID 9463 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [10/Jan/2008:19:12:35 -0500] PID 9464 (/usr/lib/cups/backend/hp) crashed on signal 9!
E [10/Jan/2008:19:15:38 -0500] PID 10027 (/usr/lib/cups/backend/hp) crashed on signal 9!
E [10/Jan/2008:19:15:39 -0500] PID 10026 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2008:19:23:51 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [10/Jan/2008:19:24:13 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [10/Jan/2008:19:24:13 -0500] PID 10053 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2008:19:24:13 -0500] PID 10054 (/usr/lib/cups/backend/hp) crashed on signal 9!
E [10/Jan/2008:19:24:14 -0500] Pause-Printer: Unauthorized
E [10/Jan/2008:19:24:24 -0500] Resume-Printer: Unauthorized
E [10/Jan/2008:20:23:59 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [10/Jan/2008:20:24:13 -0500] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [10/Jan/2008:20:25:10 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [10/Jan/2008:20:25:10 -0500] PID 10188 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2008:20:25:10 -0500] PID 10189 (/usr/lib/cups/backend/hp) crashed on signal 9!
E [10/Jan/2008:20:36:29 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [10/Jan/2008:20:36:29 -0500] PID 10470 (/usr/lib/cups/filter/pstops) crashed on signal 9!
E [10/Jan/2008:20:36:29 -0500] PID 10471 (/usr/lib/cups/backend/hp) crashed on signal 9!
E [10/Jan/2008:20:38:05 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [10/Jan/2008:20:38:05 -0500] PID 10598 (/usr/lib/cups/backend/hp) crashed on signal 9!
E [10/Jan/2008:20:38:06 -0500] PID 10597 (/usr/lib/cups/filter/pstops) crashed on signal 9!

---

### Post by drs305 on 2008-01-10
My problems with HP printers had to do with the URI. Notice in your Device URI it says "hp:/usb/hp_LaserJet_4250?serial=CNBXC25740"

In my case, when I got rid of the serial address it started working. For me, the correct address should have been "usb://HP/LaserJet%201000".  My printer connected to usb and not a serial port, as I believe yours does. For you, the correct address might be something along the same line. Change the "LaserJet_4250" part to "LaserJet%204250" and omit everything following that. Or try the same as my entry but changing the printer name. 

The two addresses I'd try would be:
usb://HP/Laserjet%204250"  or "usb://HP/LaserJet_4250"
or
hp:/usb/hp_LaserJet%204250

Since you have the address I'll assume you know how to get to the printer setup page.

You can run the following command to make sure ubuntu sees the usb printer:
```
lsusb
```

---

### Post by westwinger on 2008-01-10
The two addresses I'd try would be:
usb://HP/Laserjet%204250" or "usb://HP/LaserJet_4250"
or
hp:/usb/hp_LaserJet%204250

I tried all of these without success.
I could not find "susb" in the repos.

---

### Post by drs305 on 2008-01-10
```
lsusb
```
is just a terminal command to list all seen usb devices.  Note it is "lsusb" and not "susb".

sorry the addresses I supplied didn't work although I still believe your problem is related to the system looking for a serial device instead of a usb one.

---

### Post by drs305 on 2008-01-11
westwinger,

one thing I didn't mention was that after entering the new URI you need to power off your printer and then turn it back on to have the new address become effective. 

Maybe someone with an LJ 4250 will provide you with the URI they are successfully using. Good luck.

---

### Post by giorsat on 2008-01-22
the right one for me is usb://HP/Laserjet%204250

---

### Post by codifex maximus on 2008-04-14
Things I've learned about CUPS:
[http://localhost.localdomain:631](http://localhost.localdomain:631)  #Web administration of CUPS
hp:/usb/hp_LaserJet_4250?serial=CNBXC25740 #serial=CNBXC25740 is the serial number from the back of the unit.  Not a serial address of some kind or serial port.

Other Stuff:
lsusb as root is useful to locate usb devices and their identification information
usb selection in KDE Info is useful for even more USB Device info as is LinNeiborhood.

I was, for a time, mistakenly using the HP PSC 1500  driver and kept getting the "printmode mismatch with pen, tray, etc." error. This particular driver was for a Inkjet printer which is what I suspect was causing the pen, tray error - I have a LaserJET printer not an inkjet.

I've found a version of hplip-2.8.4 that contains a driver that I thought would work with my HP LaserJet P1505.  It is the /usr/share/ppd/HP/hp-laserjet_p1505n-hpijs-pcl.ppd.gz driver.  It seems to do everything perfect except actually print something.

I still haven't got my HP LaserJet P1505 printing in Linux but I have gotten rid of the errors.

Time will tell...
Codifex Maximus

---

