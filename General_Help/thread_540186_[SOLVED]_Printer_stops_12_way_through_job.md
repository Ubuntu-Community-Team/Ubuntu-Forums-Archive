---
title: "[SOLVED] Printer stops 1/2 way through job"
date: 2007-09-01
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2007-09-01
Good Morning Everyone :)I have an HP 648C Deskjet. It stops halfway through the job. This happens quite often. Can some one please maybe let me know what I am doing wrong? I have switched between the recommended drivers, also switched  USB/parallel and it still is stopping halfway through print job
Thanks,
Sally

---

### Post by linuxwizard on 2007-09-02
According to this that printer should work Perfectly
[http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_648C](http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_648C)

I searched the forum could not come up with anything on HP 648C Deskjet.

Searched for notes or issues here nothing everything should work
[http://hplip.sourceforge.net/supported_devices/inkjet.html](http://hplip.sourceforge.net/supported_devices/inkjet.html)

What I would do this is just a suggestion I would go and remove/uninstall the printer
System &#8594; Administration &#8594; Printing >  than use only USB make sure plugged in and printer is turned on > now go and add printer > System &#8594; Administration &#8594; Printing > click on Add Printer > it should auto detect printer > make sure Deskjet 648C shows in drop down menu > accept recommended driver > click forward to the point where you type in description of printer > click forward to end try test page

[https://help.ubuntu.com/7.04/printing/C/printing.html#local](https://help.ubuntu.com/7.04/printing/C/printing.html#local)

---

### Post by michael.dobrofsky on 2007-09-06
I have this problem, too on an Epson printer. Just stops halfway? No solution yet.

---

### Post by Tim Prosser on 2007-10-30
Confirm this happens for me, too.  Trying to print a large image from OpenOffice Draw, also if I convert to PDF, also if I export as jpg and print from the Gimp.  Every time the printer stops halfway through, at the same point.

Printer is an Epson Stylus Photo 870 that has worked perfectly up until Gutsy.

Any ideas?  Can't find anything in the printer logs.

Edit: As a last resort, restarted printer and machine, and problem went away.  Now that's getting a bit too much like windows!  Would really like where to start diagnosing if it happens again, other than the cups log and the system log...

---

