---
title: "printing from another computer?"
date: 2007-08-27
forum: General Help
---

### Post by dwink1217 on 2007-08-27
alright, heres what i need help on...

I have a computer running ubuntu studio. it has a dell printer hooked up, and it prints fine.

recently, i fixed up an old computer and put Xubuntu on it (this computer has no printer). I have a netgear router, and they're running on the same network and everything.

now the issue is,

i have lots of homework due tomorrow on the computer upstairs, and don't know how to get it to print from the downstairs printer.

who wants to help me out? :|

when it comes to linux, i only know basics. (loving ubuntu though.)

---

### Post by ArtF10 on 2007-08-27
Some printers (cough...my HP PSC 750 is an example...cough) does NOT have a Linux printer driver for NETWORK printing so I cannot print FROM an Ubuntu PC on a printer that is hooked up to a Windows PC.  I know, it's really frustrating.

---

### Post by dwink1217 on 2007-08-27
no. BOTH of my computers are running linux. i only run windows on my older computer so i can play some of my games.

---

### Post by ArtF10 on 2007-08-27
But what you are doing is trying to print from a Network Printer (regardless of which OS is installed) and not all printers have a Linux driver that supports Noetwork Printing,

This is where I checked:
[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

---

### Post by HermanAB on 2007-08-27
The Dell printer is hooked to an Ubuntu box through a USB or parallel cable?

Note that Linux makes all printers look like postscript printers.  Therefore printing to a printer that is hooked to a Linux machine is super easy.  Make sure that you have Samba and CUPS running on the printer PC.  Then on any other PC, you can access that printer using ipp://ip.add.re.ss/printername

Any simple postscript printer driver will work, eg Apple or HP, doesn't matter what.

Cheers,

H.

---

### Post by ArtF10 on 2007-08-27
> **HermanAB said:**
> ...Then on any other PC, you can access that printer using ipp://ip.add.re.ss/printername...

Is that in the terminal or is it through Samba/Cups?

---

