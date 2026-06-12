---
title: "print from command line"
date: 2007-11-05
forum: General Help
---

### Post by cnschulz on 2007-11-05
Hi

im running a gutsy headless server. cups clent and daemon installed. I have shared the printer and verified it is working over the network via smb and cups. I can print fine from my (windows) laptop.

I cant print from the command line... i have set the printer as default (in /etc/cups/printers.conf) but i still get this message when i use lpr: "Warning: no daemon present" 

any clues?

:)

---

### Post by cnschulz on 2007-11-05
almost answered it myself... :)

i deleted /etc/printcap and symlinked to the cups printcap file

from within /etc i issued this command: ln -s /var/run/cups/printcap printcap

i then had to set the default printer... the one listed in printcap

EXPORT PRINTER="iP4500" (in my case)

i put this environment variable in /etc/environment so it always loads.

BUT. now when i print the output is blank! driver issue? im using the guggenprint

any ideas?

---

### Post by patis on 2007-11-05
Did you install the cupsys-bsd package? If not, install it to see if it makes a difference.

---

### Post by Djembe on 2007-11-27
> **cnschulz said:**
> almost answered it myself... :)

i deleted /etc/printcap and symlinked to the cups printcap file

from within /etc i issued this command: ln -s /var/run/cups/printcap printcap

i then had to set the default printer... the one listed in printcap

EXPORT PRINTER="iP4500" (in my case)

i put this environment variable in /etc/environment so it always loads.

BUT. now when i print the output is blank! driver issue? im using the guggenprint

any ideas?

Currently, the Canon PIXMA iP4500 is only supported in Linux by a program called TurboPrint.  You can find a .deb install from their website [http://www.turboprint.info/](http://www.turboprint.info/)

However, there is a catch- anything you print in standard or high resolution (600dpi or higher) will have a rather large Turboprint logo on it obscuring some of the printed image unless you pay them.  However, lower resolution (300dpi) prints fine and is not obscured by a logo, which means that text printing is fine, but for photo printing, you'll either need to put up with their logo, pay them so it doesn't appear, or wait for a different driver.

---

### Post by sunstriker on 2008-05-12
You could try another driver. I use the MP150 gutenprint driver for my MP450, works fine...

---

### Post by cnschulz on 2008-05-12
SOLVED:

the native linux canon drivers have been out for ages.

thanks anyway

---

