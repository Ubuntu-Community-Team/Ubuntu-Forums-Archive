---
title: "new printer - which one for feisty?"
date: 2007-05-01
forum: General Help
---

### Post by smurphs on 2007-05-01
Hi. I'm buying a new all-in-one printer, but have read about the difficulties with them under linux. Can anyone recommend a new all-in-one printer that they know works with feisty? 

I'd prefer a HP, Canon or Epson (I'm not going within several miles of a lexmark!) All I need is the ability to photocopy and read cards (not bothered about a screen). My budget is £100.

Thanks very much,

Dylan.

---

### Post by barney_1 on 2007-05-01
You could take a look here:

[http://doc.gwos.org/index.php/Print]("http://doc.gwos.org/index.php/Print")

---

### Post by bollix47 on 2007-05-01
I have an HP Officejet 5610 all-in-one and it seems to work well with [HPLIP]("http://hplip.sourceforge.net/install/install/index.html") in Feisty and the price was within your budget.  It's by no means HP's latest printer but will do what you're asking about.

---

### Post by modorf on 2007-05-01
> **bollix47 said:**
> I have an HP Officejet 5610 all-in-one and it seems to work well with [HPLIP]("http://hplip.sourceforge.net/install/install/index.html") in Feisty and the price was within your budget.  It's by no means HP's latest printer but will do what you're asking about.

I have the OfficeJet 7310,  a little fancier than the 5610.  Using HPLIP, it works excelently.  The main difference between the two printers is duplexing on print and scan.

---

### Post by Rui Pais on 2007-05-01
Go for HP or Epson. Canon usually is the worst supported, HP the better.

I have a Epson DX5000 all-in-one and work greats, either printer and scanner.

---

### Post by smurphs on 2007-05-01
the dx 5000 sounds very tempting, and it's good to hear from someone that it actually works! I used to have an epson and was fed up with continually having to clean the print heads. Is this still an issue or have they sorted it?

---

### Post by Rui Pais on 2007-05-01
> **smurphs said:**
> the dx 5000 sounds very tempting, and it's good to hear from someone that it actually works! I used to have an epson and was fed up with continually having to clean the print heads. Is this still an issue or have they sorted it?

I haven't yet a single problem with it. Using for direct photocopy, print docs (bw/color), print photos from computer and from camera. The only thing down (probably common to all printers) is the rate of ink consume goes exponential when printing photo, and probably there is more economic choices available... 
Never cleaned the headers until now (3 month of use).

---

### Post by smurphs on 2007-05-01
cheers all. think i'll go with the epson dx 5000, as it seems to have a good spread of reviews (and i'm a tight-****!)

thanks all.

dylan.

---

### Post by Rui Pais on 2007-05-01
well, i was just giving my experience, but if you want to make your mind so quickly :)

here is a [mini how-to]("http://ubuntuforums.org/showthread.php?p=2564893") on eventually some problem that you may find. 

There is no specific driver for it yet. It works with driver for CX5800 or DX4800.

There is some close source drivers (not payed!) too, that give an extra little bit of quality with photos, if you want to try. They have too a nice app too, called iscan, that it's more easy to use then xsane, but with less option...

Good luck.

---

### Post by ubuntu27 on 2007-05-01
> **smurphs said:**
> cheers all. think i'll go with the epson dx 5000, as it seems to have a good spread of reviews (and i'm a tight-****!)

thanks all.

dylan.


Double check that the printer that you want to buy is compatible with Linux. Check the following:

[List of HP Printers support in GNU/Linux]("http://www.linuxprinting.org/printer_list.cgi?make=HP")

[List of EPSON Printer compatibility with Linux]("http://www.linuxprinting.org/printer_list.cgi?make=Epson")

---

### Post by wyth on 2007-05-01
This may not server your needs, but I just picked up a Brother HL-2070n laser network printer for $100 US (with rebate).  It works flawlessly with linux; the company offers linux support and drivers.

---

### Post by smurphs on 2007-05-15
Got an Epson DX5050 and it works flawlessly if anyone else is interested. The printer works with the epson dx4800 driver built into ubuntu. to get the scanner to work with xsane, you need to do this:


- Add in /etc/sane.d/epson.conf
usb 0x04b8 0x082b

- And then.. add in /etc/udev/rules.d/45-libsane.rules
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082b", MODE="664", GROUP="scanner"

then reboot.

very happy with the print quality - matches my old photo 750 even though it only has the 3 colours. Bargain at £50 from staples too. Staples even let you return in 14 days if you're not happy with it (god bless 'em - Dixons laughed when I asked if they do the same!)

dylan.

---

