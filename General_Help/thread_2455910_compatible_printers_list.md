---
title: "compatible printers list?"
date: 2020-12-30
forum: General Help
---

### Post by logie on 2020-12-30
I am looking for a budget printer/scanner for home use.  I need it to work with Ubuntu 18.04 onwards.  Is there a list, or information about which ones are readily compatible?

---

### Post by SeijiSensei on 2020-12-30
Since you are looking for scanners, I suggest you start here. [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

Most Brother and HP models are compatible. I've seen more issues reported by Canon and Epson owners.

I have an HP Scanjet 4850 which was not supported by SANE. Now it is recognized by the Skanlite software that comes with Kubuntu 20.04.  Still I prefer to use VueScan: [https://www.hamrick.com/](https://www.hamrick.com/)

---

### Post by rsteinmetz70112 on 2020-12-30
I find that most HP models are supported including all-in-one models. you can check the HPLIP list of [supported models]("https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index"). If a precise model is not on the list sometime there are workarounds.

---

### Post by Autodave on 2020-12-30
+1 with HP printers.

---

### Post by logie on 2020-12-31
Thanks for your quick reply - but I don't understand it..

---

### Post by logie on 2020-12-31
Thanks for your speedy reply.  I think I have misled you. I am not looking for separate printer and scanner, but would prefer an all-in-one. My last printer was with me for over 15 years, and my scanner about the same, so I have completely lost track of what works and what doesn't.

---

### Post by dino99 on 2020-12-31
Nowadays all these devices work by default with linux; myself using all-in-one since years on ubuntu  :p

---

### Post by rsteinmetz70112 on 2020-12-31
What don't you understand?

---

### Post by logie on 2021-01-01
Sorry: it's not the reply from rsteinmetz, but the one from autodave that I don't understand. Sorry again.

---

### Post by TheFu on 2021-01-01
> **logie said:**
> Thanks for your speedy reply.  I think I have misled you. I am not looking for separate printer and scanner, but would prefer an all-in-one. My last printer was with me for over 15 years, and my scanner about the same, so I have completely lost track of what works and what doesn't.

For your consideration, 

Inkjet printers tend to cost more in ink annually than the printer is worth.  OTOH, if you get a cheap laser printer, the toner will last 10 yrs (or run out).  Then you are just back to the scanner issue.

I have a Brother All-in-One from around 2008. It has automatic sheet feed scanner, fax, inkjet printer. The scanner works fine connected to a 16.04 server here. Using **gscan2pdf** most of the time with it. It faxes some govt documents a few times a year and can write the scanned files to SDHC storage or get pulled into that app. After the 50 page initial ink cartridge dried out, I never replaced it and never plan to replace it.  It is USB.  

Have Samsung laser printer too.  It is on the 2nd toner cartridge in about 15 yrs. I shake the toner yearly to keep the output even. Bought a 10,000 pg cartridge to replace the 2K pg one it came with. This is also USB. The printer has been in the Linux printer list for a long time. It is connected to the same 16.04 server and CUPS/IPP networking lets other systems access it.  A new 20.04 install took all of 15 seconds to get printing.  20.04 --[LAN]--> 16.04(IPP+cups) --[USB]--> Samsung Laser --> Paper

For printing, IPP and postscript are the most certain ways to print. Any postscript file can be sent to any postscript printer.  The laser printer is fantastic and I wouldn't trade it for any inkjet. Usually after 18 months, the slightly greater cost of a laser printer is paid for by avoiding inkjet refills - that's a racket.

And I'd avoid wifi in any printer/scanner.  Stick with USB and/or wired networked devices. Wifi always seems to have issues.

---

### Post by logie on 2021-01-03
Thanks to TheFu for this.  This is full of useful information, in particular it has made me think of getting a laser printer. Yes indeed, and thanks again.

---

### Post by ActionParsnip on 2021-01-03
Bit late to the party but +1 for HP

---

