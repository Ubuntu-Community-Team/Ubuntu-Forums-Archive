---
title: "Will an Epson AcuLaser™ CX11N work with Ubuntu?"
date: 2006-11-27
forum: General Help
---

### Post by Staz70560 on 2006-11-27
I was going to buy my wife an [Epson AcuLaser™ CX11N]("http://www.epson.com/cgi-bin/Store/consumer/consDetail.jsp?BV_UseBVCookie=yes&infoType=Overview&oid=58311372&category=Products") for Christmas. But she has completely switched over to Ubuntu (and hates Bill Gates) and I need to know if it will work.

Thnx in Advance
Maurice

---

### Post by ReaderRat on 2006-11-27
Couldn't find it (take a look)....
[**Epson Printers**](http://www.linuxprinting.org/printer_list.cgi?make=Epson)

You can find out a lot about peripherals by looking them up In the Hardware Compatibility List (below in my signature).

---

### Post by Juxi on 2006-12-19
I know of ppl that made it run under Xubuntu, but I dunno how they did it...

---

### Post by Juxi on 2006-12-19
I got it to work:
1) download the drivers from [http://www.avasys.jp/lx-bin2/linux_e/mfp/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/mfp/DL2.do) (I took the i386)
2) conver the rpms to deb files with "sudo alien --scripts *.rpm"
3) a) install the filter file with "sudo dpkg -i something-filter-11.deb" 
3) b) install the filter-cups file with "sudo dpkg -i something-filter-cups-11.deb" 
4) create the printer with your cups-manager

I have not yet got the scanner to work over the network (USB connected it should not be a problem, although I have not tried that, since the printer is on another floor ;))

---

### Post by lsilver on 2007-05-21
Has anyone got this printer working on Fiesty?

---

### Post by thomas_perso on 2007-10-01
Hi Juxi,

you say 

> download the drivers from [http://www.avasys.jp/lx-bin2/linux_e/mfp/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/mfp/DL2.do) (I took the i386)

For KUBUNTU, CUPS, what do you prefer to use,

Turbo/RedHat/Fedora

or

SuSE/Mandrake

([http://www.avasys.jp/english/linux_e/dl_mfp.html]("http://www.avasys.jp/english/linux_e/dl_mfp.html"))

Thanks !
Thomas

---

