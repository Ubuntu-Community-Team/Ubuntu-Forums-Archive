---
title: "missing cups/filter file"
date: 2020-10-11
forum: General Help
---

### Post by john-fanmaker on 2020-10-11
Running 16.04 on a 32bit laptop, with Epson WF-2650 printer.
Quote - Printer WF2650 requires the '/usr/lib/cups filter//opt/epson-inkjet-printer-escpr/cups/lib/filter/epson-escpr-wrapper' program but it is currently not installed -unquote.
Went to my files and sure enough this is not in the cups/filter folder.
Can someone tell me 1. The significance of the // in the file name, and 2. Where do I find that file.

I tried going via the troubleshooting menu, and got as far as searching for the driver, and I thought it had installed it, so I re-started, and tried the printer, but no luck.

I'm happy to use Terminal to download and install, but I don't know what I need to download.
Regards all,
John

---

### Post by TheFu on 2020-10-11
// is the same as / or ////////// in the unix paths.  Because it doesn't matter, nobody cares and wouldn't bother fixing a config file that has an extra one at the, then gets concatenated with some other path along the way.

Since
```
/path/to/dir[COLOR="#FF0000"]/[/COLOR]    +   /some/other.file = /path/to/dir[COLOR="#FF0000"]/[/COLOR]/some/other.file 
```
then it isn't really worth fixing, right?

No clue about your printing issue. sorry.  I use cups with my usb printer and it all works.  Remote computers point at the ubuntu system running cups. I use the IPP protocol. Drivers for my printers gt loaded the first setup. Pretty easy the last 8 yrs or so.  But I don't use non-USB printers.

---

### Post by john-fanmaker on 2020-10-11
Hi TheFu, and thanks for the heads up re slashes. Mine is a usb printer, though I have it currently configured to work wirelessly.
I've tried re- connecting it via usb and tried another install, but after trying a reboot, still no joy.
There does seem to have been a problem with printers when 16.04 first came out, but mine has been working without this sort of problem up to the beginning of last week , which makes it more puzzling.
Regards
John

---

