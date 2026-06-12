---
title: "Printing multiple pages on one sheet does not work"
date: 2007-01-10
forum: General Help
---

### Post by jhs_s on 2007-01-10
Hi!

I wanted to print two pages on one sheet (same side) with evince and selected that in the printer dialog. Anyway, I did not work, the printer always printed each page on one sheet.

I tried this with two printers:
- HP Laserjet (over SMB)
- Samsung ML-2010 (local USB)

Is there anything else I have to do to make this work?

Thanks,
Johannes

---

### Post by tweedledee on 2007-01-10
> **jhs_s said:**
> Hi!

I wanted to print two pages on one sheet (same side) with evince and selected that in the printer dialog. Anyway, I did not work, the printer always printed each page on one sheet.

I tried this with two printers:
- HP Laserjet (over SMB)
- Samsung ML-2010 (local USB)

Is there anything else I have to do to make this work?

Thanks,
Johannes

Your printer driver needs to support this.  Can you successfully print this way from another program?  I have found that 1) without setting the printer (on the printer console, not via software) to print multiple pages per page, it doesn't work in Ubuntu, and 2) evince is still a bit quirky with printing.

---

### Post by xodut on 2007-01-11
I can confirm with LaserJet 1000. Anyway, you should find in the last tab in (GTK) printing dialog column called N-up printing, which works, but it's buggy :-(

The second problem is printing to file -- I can't set-up multiple pages per sheet

The third problem is unavailability to print to pdf file.

The only solution now is installing kpdf, where everyting just works.

I think, this should be reported as bug, but I don't know where :-\

---

### Post by tweedledee on 2007-01-13
> **xodut said:**
> I can confirm with LaserJet 1000. Anyway, you should find in the last tab in (GTK) printing dialog column called N-up printing, which works, but it's buggy :-(

The second problem is printing to file -- I can't set-up multiple pages per sheet

The third problem is unavailability to print to pdf file.

The only solution now is installing kpdf, where everyting just works.

I think, this should be reported as bug, but I don't know where :-\

If you can get it to work kpdf but not evince, then either file a bug on the Gnome Launchpad site, or contact the Evince team ([http://live.gnome.org/Evince/Team)](http://live.gnome.org/Evince/Team)).

As for printing to a pdf file, have you install cups-pdf?  That provides a pdf printer.

---

