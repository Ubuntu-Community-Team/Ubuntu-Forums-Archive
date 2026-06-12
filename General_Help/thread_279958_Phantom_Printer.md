---
title: "Phantom Printer"
date: 2006-10-18
forum: General Help
---

### Post by localuser on 2006-10-18
I have a printer listed in my Printers dialog (System | Administration | Printing) which I can't remove.

I originally turned on "Detect LAN Printers" under the Global Settings menu item and the system added several LAN printers.  I then turned off "Detect LAN Printers" and tried to delete each of the printers which were added.  There is one printer, however, that refuses to get deleted.  It simply ignores my Remove command (naughty printer).

Which file does this dialog manipulate?  I wonder if manually deleting the entry in the appropriate file might help.  Or perhaps not and there is something else I should do.

I'm running version 6.06

Thanks,

~lu

---

### Post by mssever on 2006-10-18
You might try going to [http://localhost:631](http://localhost:631) and removing the printer from there.

---

### Post by localuser on 2006-10-31
> **mssever said:**
> You might try going to [http://localhost:631](http://localhost:631) and removing the printer from there.

This is really annoying.  Not only do I now have a phantom printer, but now its got 3 pending print jobs and I can't get rid of the jobs or the printer itself.  Went into localhost:631 and when I try to remove it I get an error screen stating that the server can't be found.

The properties for this printer shows it as an CUPS Printer (IPP).
 
There must be a file somewhere in the system which I can manually edit.  Does anyone know where that file might be?

I'm to the point of having to reinstall the system and I really don't want to do that as that would be very Microsoft-ish.

---

### Post by mssever on 2006-10-31
Try /etc/cups/printers.conf and /etc/cups/ppd. Be sure to restart cups afterward.

---

### Post by localuser on 2006-10-31
> **mssever said:**
> Try /etc/cups/printers.conf and /etc/cups/ppd. Be sure to restart cups afterward.

The only thing which shows up is the legitimate Epson printer.

**ppd:**
total 80
drwxr-xr-x 2 cupsys lp  4096 2006-10-18 09:11 .
drwxr-sr-t 6 cupsys lp  4096 2006-10-31 14:32 ..
-rw-r--r-- 1 cupsys lp 66395 2006-10-18 09:11 Stylus-C84.ppd

**printers.conf:**
# Printer configuration file for CUPS v1.2.2
# Written by cupsd on 2006-10-31 14:32
<Printer Stylus-C84>
Info Stylus-C84
DeviceURI usb://EPSON/Stylus%20C84
State Idle
StateTime 1161188038
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>

---

