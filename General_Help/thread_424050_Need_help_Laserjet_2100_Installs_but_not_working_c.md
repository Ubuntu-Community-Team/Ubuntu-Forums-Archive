---
title: "Need help Laserjet 2100 Installs but not working correctly"
date: 2007-04-26
forum: General Help
---

### Post by comfortablynumb on 2007-04-26
So I hooked my HP laserjet 2100 uptoday, went to printers | Add Printer and Cups detected the printer correctly and installed it. By default I tried the Postscript driver, printed a test page and it printed page after page of this:

%!PS-Adobe-3.0
                            %%Title: PPR Test Page
                                                                         %%DocumentNeedsResources: font Helvetica
                                                                                                                                                            %%F

---

### Post by comfortablynumb on 2007-04-26
I cant pint from firefox either...getting a mozilla postscript plugin error...I looked in the synaptic and don't see any plugins

---

### Post by kag on 2007-04-26
I've got the exact same printer, exact same problem occured today. I just switched the driver for another one.

---

### Post by phidia on 2007-04-26
Have you looked here?

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_2100](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_2100)

---

### Post by comfortablynumb on 2007-04-27
> **phidia said:**
> Have you looked here?

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_2100](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_2100)

Thanks for the link, I installed that driver and restarted cups...Im getting the same exact error message.

---

### Post by comfortablynumb on 2007-04-27
Ok after digging deeper I noticed something really stupid....Where it says detected printer it had 
Laserjet2100 and underneath it
ADOBE PDF

So I selcted specify a port and selected LPT1, and it printed a test page fine.

---

### Post by phidia on 2007-04-27
This should be in a how to for printer configuration problems-I wonder why it defaults to that setting?

---

### Post by comfortablynumb on 2007-04-27
> **phidia said:**
> This should be in a how to for printer configuration problems-I wonder why it defaults to that setting?

I'm not to sure, I wish I would of thought to check that earlier, but I thought it showing the printer and selected driver was all I had to do.

I've rebooted the box to make sure the settings stick and it's still printing fine from both Opera and Firefox.

---

