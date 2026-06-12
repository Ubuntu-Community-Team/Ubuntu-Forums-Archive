---
title: "Epson FX-1170 driver"
date: 2005-09-08
forum: General Help
---

### Post by arlie on 2005-09-08
Where can I get an Epson FX-1170 driver? I tried dot matrix/ 9 pin but output is garbled.

Please help.

---

### Post by MrCheese on 2005-09-08
[QUOTE=arlie]Where can I get an Epson FX-1170 driver? I tried dot matrix/ 9 pin but output is garbled.

Please help.[/QUOTE]

Epsons use esc-p/ 2 to control print output, so try the simplest esc-p/2 driver  (such as fx80) available. Any generic text-only driver should also work. If all else fails try changing the printer emulation to IBM Proprinter or another non-esc-p/2 model.

Also check out

 [http://linux.co.uk/howtos/Printing-HOWTO/printers.html](http://linux.co.uk/howtos/Printing-HOWTO/printers.html)

You should find that simply copying screen output to lp also works (if you don''t mind formatting oddities) 

eg cat /etc/fstab|/dev/lp0 

should produce a text dump of /etc/fstab.

---

