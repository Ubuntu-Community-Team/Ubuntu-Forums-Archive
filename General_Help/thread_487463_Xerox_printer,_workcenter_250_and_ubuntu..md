---
title: "Xerox printer, workcenter 250 and ubuntu."
date: 2007-06-29
forum: General Help
---

### Post by Nevermore on 2007-06-29
Hi everyone
i have a network printer, a Xerox workcenter 250 on my network.
When i try to add a printer, ubuntu recognizes it and adds a workcenter 450 as printer.
but i can't print to it, alot of white pages with some garbled things comes out every time i try to print...how can i fix that?
i need to print!

---

### Post by tgronke on 2007-11-10
Please verify that is a Xerox Workcentre 250.  From various web searchin a little personal experience, the Workcentre 250 is a 1995-vintage inkjet multi-function device (scanner, fax, parallel printer, copier, fax modem) with no network capabilities.

The last drivers available for a Workcentre 250 from Xerox's web site were for Windows 95/98/ME.  I believe this is a PCL printer.  Xerox no longer supports the Workcentre 250.  From multiple searches for 'workcentre 250', the only possible match is using a HP Deskjet 500 driver or equivalent.

The Workcentre 245 or 255 are networked laser-printing multifunction devices (scanner, fax, high-speed LAN printer, USB printer, high-speed copier, LAN fax, some email capabilities).  The printer appears to support multiple print descrption languages (PCL, Postscript, TIFF, PDF)

Xerox's web site has current drivers for the Workcenter 245 or 255, including Linux and various Unix flavors.  I do not have experience with these printers or drivers on Ubuntu.

---

### Post by derjur on 2007-11-29
do you mean a docucolor 250?
These are recent network printers similar to the WCP 7655

They use a driver and interface system known as Fiery which works great from a windows machine.  I'm having a few issues trying to get it to work from Ubuntu.  If you're asking about the same printer, I will post my progress here.

---

### Post by derjur on 2007-12-06
Ok, this turned out to be easy.


If it's a network printer, you can simply go to "System->Administration->Printing"
Select "New Printer"

Let it search your network for printers.  I'm not sure if it does this by ip/port scan, or if it loads by AD or both.  It seemed to have detected both AD printers and printers that were network shared, but not in AD.  It takes a minute or two either way.

When it'd finished, you select the printer you want from the list.  

When asked for a driver, select Generic, then Postscript and Generic PostScript Printer (recommended).  Set your settings, and click apply.

I would imagine that this works with all postscript printers, as it seems to be working for all of my Xerox and IBM printers here.  YMMV.

---

