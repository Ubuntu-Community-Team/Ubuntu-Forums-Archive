---
title: "Is re-installing the printer the best route ?"
date: 2021-05-06
forum: General Help
---

### Post by grey1beard on 2021-05-06
My Epson Workforce 2650 printer has been working well for the last couple of years, even through various upgrades to my system, and recently to work as a network printer for my desktop as well as the laptop.
Yesterday fine. This morning I deleted two instances of InkMagick which didn't load, and installed mtPaint in their place.

I latter tried to print an article from the net, and got nothing from the printer.
Checked the System Settings/Printers/Properties/Settings/Printer State: Stopped - Backend /usr/lib/cups/backend/dnssd does not exist!

I've done some exploring, and it seems to be true. However, the more I google for a solution, the more confused I get.

I'd be grateful for a simple solution if there is one, but coming to the conclusion that deleting the printer and re-installing might be the only way to go.

John :(

---

### Post by grey1beard on 2021-05-07
With no help forthcoming, I've spent the last couple of hours going round in circles.
I did re-install it, but got back to the same problem.
Further searching brought me to a suggestion of ** sudo apt install printer-driver-gutenprint** as it would install several drivers for various printers.
Sure enough, there was dnssd in its proper place.
A quick test print, and I'm up and running once more.
John

---

