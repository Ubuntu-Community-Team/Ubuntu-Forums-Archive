---
title: "no printing"
date: 2005-04-25
forum: General Help
---

### Post by paulle on 2005-04-25
abiword, gnumeric and gimp don't print. maybe it's a problem with cups.
I've a Hp-usb connected printer.
Anybody encountered the same problem?

---

### Post by DutchLau on 2005-04-26
Hi Paulle,

I've just installed my HP 5150C Deskjet with Ubuntu. It seems to work well - but only AFTER I got the official drivers installed from HP. Perhaps this has something to do with the printer driver not being supported by cups. I'm an uber noob with Linux  :smile:  so I've warned you. If you inflict any damage upon your PC it's not my fault!

Take a look at this website by HP. [http://hpinkjet.sourceforge.net/productssupported.php](http://hpinkjet.sourceforge.net/productssupported.php) and see which type of driver is best for your printer. Now go to [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi)  Download the .PPD file and now in Gnome set up your printer. Go to System => Administration => Printing. Add a New printer, follow the steps (Use detected printer) Choose the model, Press "Install Driver" and find the .PPD file you saved. This should successfully install the printer. Restart cups, or reboot the computer, either works.

Let us know if it worked! 

Cheers,

EDIT: Missing step

---

### Post by paulle on 2005-04-26
hi dutchlau, thanks for your hint, I will try it.
But i've now the impression it's a problem with cups or because it's usb-connected printer.

thanks a lot                                                    paulle

---

### Post by DutchLau on 2005-04-26
Hi again Paulle,

My HP 5150C is also a usb-printer and Ubuntu detects it perfectly. Could you print *at all* before you started this thread? Let me know if my "howto" worked  :)

---

### Post by paulle on 2005-04-26
hi dutchlau, yes i could print with warty. no i can't print. the problem is that the system-administration-printing dont accept my locacal hp640c as an usb-connected printer, it's always reset it as a not usb connected printer. tried out all and reinstalled cups, but always the same.

ciao paulle

---

### Post by DutchLau on 2005-04-26
Looks like a bit of a problem. I also have a 615c and a 640c that I plan on installing sometime soon, but when I'm done doing that (and if I succeed) I'll post again,

Cheers

---

### Post by paulle on 2005-04-26
hi dutchlau,
ok let me know, especially when usb-connected.    thanks  paulle

---

