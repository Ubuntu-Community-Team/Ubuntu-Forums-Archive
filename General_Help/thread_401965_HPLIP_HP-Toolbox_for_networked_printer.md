---
title: "HPLIP HP-Toolbox for networked printer"
date: 2007-04-05
forum: General Help
---

### Post by rosbif on 2007-04-05
I have an HP7210 MFD running just fine as a printer, connected via the network (this model has a direct ethernet connection).  I can print just fine via CUPS/HPLIP (and can view printer settings via [http://localhost:631)](http://localhost:631)), however, when I start the HP-Toolbox utility which comes as part of HPLIP,  it can't find the printer and there seems to be no config for it.  Any clues?  I'm running Edgy, CUPS 1.2.4 and HPLIP 1.6.9

---

### Post by 11hjpphty76lkjj on 2007-04-05
If you configured the printer using cups the printer is probably not configured to use the HP backend.  Try running hp-setup to configure the printer.  

You also may want to consider updating to the latest hplip as well.

[http://hplip.sourceforge.net](http://hplip.sourceforge.net)

A

---

