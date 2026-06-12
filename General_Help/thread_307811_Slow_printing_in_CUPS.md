---
title: "Slow printing in CUPS"
date: 2006-11-27
forum: General Help
---

### Post by frisket on 2006-11-27
I have Edgy on my Inspiron laptop: pretty much everything works, but CUPS prints at about 1/10 normal speed. 

I have a HP DJ 1220C attached to the parallel port. CUPS didn't find it, so I created a new printer and told it. It print a pass of the printhead, waits for a few seconds, then another pass, and another wait, etc, just as if it was on a 10cps serial connection. 

I plugged the printer into the USB port and changed the config to match, but there is no difference in speed. Obviously I've got something wrong, but what? 

Print was working fine under my previous FC4, despite CUPS, and Mac and Win toting guests have no problems if they plug into it.

///Peter

---

### Post by scooper on 2006-11-27
This won't be very helpful, but it probably has something to do with it getting interpreted by the postscript interpreter (gs?) for output.  You may have the wrong print driver installed, e.g. one that interprets the postscript rather than just passing it to the printer.  I'm interested in hearing the solution, since I haven't set up my printer, and have also had slower printing speeds in the past.

---

### Post by frisket on 2006-11-27
According to the Properties, it's using the hpijs driver (recommended). I don't know if this calls on gs as an intermediary or not. The spooling speed (time from click to first printhead movement) seems about right (3-4 sec), but it then chugs along as if it's an elderly dot-matrix pin printer with those delay loops we used to write to accommodate slow printhead returns :-) What's puzzling is that this is a fresh-out-of-the-box vanilla Ubuntu install with no mods.

This never used to happen with lprNG, which flew like a bird and never dropped a bit (but didn't have the drivers to switch from 300dpi to 600dpi, for example).

I just tried printing a page image in GIMP, though, having done a setup for a HP 1220C in GIMP's own printer config, and it prints at normal speed. Tentative conclusion is that there's something screwy in the CUPS config, which would mean a bug in CUPS.

---

### Post by ReaderRat on 2006-11-27
You might try the HPLIP driver which includes the HPIJS driver in it....
**[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_1220C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_1220C)**

---

### Post by windwalker78 on 2006-12-11
Hi Everybody,

You can try editing your printers.conf in /etc/cups/ , like this:

DeviceURI file://dev/usblp0

It resolved similar problem with my Minolta 1400W

Regards,
Todor

---

### Post by frisket on 2006-12-19
> **scooper said:**
> This won't be very helpful, but it probably has something to do with it getting interpreted by the postscript interpreter (gs?) for output.  You may have the wrong print driver installed, e.g. one that interprets the postscript rather than just passing it to the printer.  I'm interested in hearing the solution, since I haven't set up my printer, and have also had slower printing speeds in the past.

The driver is the recommended HPIJS one. It's not a PS printer, so sending it raw PS will simply result in it printing PS code...

---

