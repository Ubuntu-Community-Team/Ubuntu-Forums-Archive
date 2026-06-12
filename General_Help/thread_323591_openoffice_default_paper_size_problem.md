---
title: "openoffice default paper size problem"
date: 2006-12-22
forum: General Help
---

### Post by jdh on 2006-12-22
In openoffice 2.0.2 I have problem with the my printer not printing correctly. Because every time I open a new document (any type), the default paper size for the printer gets changed to A4. This also changes the printer default paper size that was set by spadmin from letter to A4. Default printer is a HP color laserjet 2550n, using the postscript driver. How/where do I set the openoffice default paper size to letter?

---

### Post by tagra123 on 2006-12-22
> **jdh said:**
> In openoffice 2.0.2 I have problem with the my printer not printing correctly. Because every time I open a new document (any type), the default paper size for the printer gets changed to A4. This also changes the printer default paper size that was set by spadmin from letter to A4. Default printer is a HP color laserjet 2550n, using the postscript driver. How/where do I set the openoffice default paper size to letter?

Try changing it in System Administration Printing  and changing the paper sie there for your printer.  I think this is how I got it to work correctly. For documents already saved as an A4 -- some of them may still need adjusted to 8.5 X 11. but most of them now default to letter size.


This is one of the annoying things. If I select US English it would be nice if the installer could manage that 8.5" X 11" LETTER is what we use.

---

### Post by jdh on 2006-12-22
> **tagra123 said:**
> Try changing it in System Administration Printing  and changing the paper sie there for your printer.  I think this is how I got it to work correctly. For documents already saved as an A4 -- some of them may still need adjusted to 8.5 X 11. but most of them now default to letter size.


This is one of the annoying things. If I select US English it would be nice if the installer could manage that 8.5" X 11" LETTER is what we use.
This is set correctly to letter and does not change. Openoffice does not use the system settings. I set the default to letter using spadmin when setting up the printer in openoffice, it has no effect after opening a new document. I can go into spadmin and change it but it will not stay changed.

---

### Post by wes-sole on 2006-12-24
> **jdh said:**
> This is set correctly to letter and does not change. Openoffice does not use the system settings. I set the default to letter using spadmin when setting up the printer in openoffice, it has no effect after opening a new document. I can go into spadmin and change it but it will not stay changed.

Operating system: Ubuntu 6.06LTS, Openoffice 2.0.2
Printing from Firefox, Thunderbird, Evince 0.5.2 and other utilities is ok but I have the same problem as jdh has when printing from Openoffice.  In addition, which may help resolve the problem source, when I press the "Print a Test Page" button in the printer setup the printer displays "PC LOAD A4".  The printer is an HP LaserJet 4 and the printer setip follows: System>Administration>Printers:
  LaserJet-4 Properties:
     Paper>Paper size: Letter
     Advanced>PageRegion: Letter
     Driver>HP>LaserJet 4   hpijs(recommended) driver installed
     Connection>Network Printer: UNIX Printer (LPD)
          Host: 192.168.2.1
          Queue: LPT1
Connection is to an SMC "BARRICADE" SMC7004ABR

---

### Post by koolkatkiwi on 2007-12-08
Ha! I have exactly the opposite problem! I have an HP Laserjet 4 and I want it to always print A4 size - our standard paper size here. But that OpenOffice.org program insists on setting it to Letter unless I change it on each new page I make. The solution would solve both our problems.

Cheers,
Kath:KS

---

### Post by koolkatkiwi on 2007-12-08
OK!!! Now we're cooking with gas! Just follow this tutorial and you can change your default page settings to whatever you like, including the default font, which I changed to Arial as I hate Times Roman.

[http://www.nabble.com/Change-paper-size-setting-to13881642.html](http://www.nabble.com/Change-paper-size-setting-to13881642.html)

It seems unnecessarily complex, unintuitive, and hard to find out how to do it, but it is really simple to do, once you find out! I would like to ask the program developers to make it possible to change the default page settings easily - say up in the "default" box or the "styles and formatting" box in the left hand corner.

I can't mark this thread as SOLVED, as I didn't start the thread, but I consider it solved now anyway.

Cheers,
Kath:KS

---

### Post by koolkatkiwi on 2007-12-08
Just in case that other link should disappear, here's the official one:

[http://www.oooforum.org/forum/viewtopic.phtml?t=802](http://www.oooforum.org/forum/viewtopic.phtml?t=802)

Cheers,
Kath:KS

---

### Post by rpremuz on 2007-12-14
In short, the solution is to create a new document template and use it as the default.
See: Help -> Index tab -> entries under "default templates".

The solution would be easy to find if the OpenOffice help had an entry about "default page" or "default document template" that would point to instructions about default templates.

-- rpr.

---

### Post by danielrudas on 2008-01-17
I have the same problem with Ubuntu 7.10, OpenOffice 2.3 and a Canon Pixma iP1500.

I found here something:
[https://lists.ubuntu.com/archives/ubuntu-users/2005-October/053149.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-October/053149.html)

They talk about a file:  '/etc/papersize' . So just open it and edit the paper size.

gksudo gedit '/etc/papersize' 
 
I just change "a4" for "letter" and restart OpenOffice. The problem was fixed.

---

### Post by rkh on 2008-03-08
Thank you! This problem was driving me crazy!  I searched the OO.o forums and kept on finding posts telling me to save a blank page set to letter (rather than A4) as the default template. That is exactly what you should do if you want to change the default page setting. If you want to change the default  print setting (which should be automatic-every other program seems to understand what the way I set it up in System-Administration-Printing, just not OO). 

gksudo gedit '/etc/papersize'

---

