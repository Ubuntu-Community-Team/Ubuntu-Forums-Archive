---
title: "HP Laserjet not showing in Xenial Xerus"
date: 2018-02-17
forum: General Help
---

### Post by ianadkins on 2018-02-17
Hi all,

New again to Ubuntu.  I last ran it for a year under Hardy Heron.  Current version is Xenial Xerus.

I have an HP Laserjet P1102W that does not show up when plugged into any three of my USB ports.  Look for it under Printers, and bupkes.

Following some advice elsewhere I downloaded HPLIP from HP.  Ran hp-setup -i in terminal, it asked for input source, I selected USB, and it said no device found,

Now, I plug in a USB speaker or thumb drive, and they work fine.

Ran lsusb:

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2c55 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 012: ID 03f0:032a Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I think it's interesting the second to last item said Hewlett-Packard, but I don't know what that might signify.

If it helps to know, this printer was working just last week under Windows 10. 

Thank you!

---

### Post by ajgreeny on 2018-02-17
A downloadable driver plug-in is required for printing support with that printer.

The HPLIP site says:-
8 ("Required") A downloadable driver plug-in is required for printing support. ("Optional") A downloadable driver plug-in is optional for printing support and may increase the speed, quality, or other aspect of printed output. ("No" or "None") A driver plug-in is not required nor available. Driver plug-ins are released under a proprietary (non-open) license and are not part of the HPLIP tarball release. For more information, please refer to this [KB article]("https://developers.hp.com/hp-linux-imaging-and-printing/binary_plugin.html")

I've never needed to download one of these plugins so can't help you with any more details or experience.

---

### Post by ianadkins on 2018-02-18
Hi AJ,

I saw that I had at least the minimum version of HPLIP installed, but not the latest.  I don't remember what side search I did or why (like a hundred tabs open), but I found this page:

[https://sites.google.com/site/tipsandtricksforubuntu/printer-info/hplip-driver](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/hplip-driver)

So I actually downloaded HPLIP from the HP site, made it executable (first time I've ever done that), and it ran beautifully.  Restarted, plugged in the printer, it prompted me to install a plugin, installed it, and we were off to the races.  I have in my hands a hot, freshly printed PDF.

Thank you for your help!

---

### Post by ajgreeny on 2018-02-19
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

