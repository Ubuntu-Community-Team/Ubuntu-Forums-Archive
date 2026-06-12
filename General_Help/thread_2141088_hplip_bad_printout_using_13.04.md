---
title: "hplip bad printout using 13.04"
date: 2013-05-01
forum: General Help
---

### Post by scottme on 2013-05-01
I'm trying to print my latest American Express statement - it's a PDF file and there are a number of fields where numbers are presented on a shaded background - the screencap fragment below shows what they look like: 
[IMG]https://dl.dropboxusercontent.com/u/8544987/AmexField.png[/IMG].

I never had any trouble printing these statements before, but I just installed Raring and now those fields are printing as solid black blocks - same result on both my HP printers (an OfficeJet 6300 and a LaserJet 6MP). They both work faultlessly on my 12.10 installation, which has hplip 3.12.6-3.  My 13.04 install has hplip 3.13.3-1.

I can't find any other reports of this problem. Where should I go looking for guidance or a workaround, and/or where can I raise a bug report on this?

---

### Post by Mark Phelps on 2013-05-02
Can't advise you regarding HPLIP as I don't use it.  I've used several different HP printers over the years and have always found that CUPS is able to handle them well using its own drivers.

IF you want to experiment with CUPS, open a browser, enter "localhost:731" and use the menus to install a printer.

---

### Post by scottme on 2013-05-02
I am using CUPS (1.6.2-1), and both my HP printers are already defined to it. I can send printout to them no problem. The problem is how certain parts of the printout appear.

I had a strong feeling that the problem must lie in hplip, which in my experience (up to now) is the best driver software for the HP printers. When I say "driver", I mean that it is responsible for rendering the pages into a suitable data stream for the printer to use.

Then I changed my Laserjet settings to use a different driver (Gutenprint), and I was still getting the black boxes. So I installed a different PDF viewer, Okular, and when I print from that the pages with the shaded boxes come out OK. So I have changed my mind and I now think the problem lies in Evince, the default Ubuntu PDF viewer application.  Raring uses evince 3.6.1, and it looks like Quantal (where it works OK) has 3.4.0.

---

### Post by Sef on 2013-05-02
> [COLOR=#000000]So I installed a different PDF viewer, Okular, and when I print from that the pages with the shaded boxes come out OK. So I have changed my mind and I now think the problem lies in Evince, the default Ubuntu PDF viewer application.[/COLOR]

The problem is with Evince since Okular prints ok. Have you filed a bug report in [Launchpad]("https://launchpad.net/")?

---

### Post by tgalati4 on 2013-05-02
Open [http://localhost:631](http://localhost:631) and bring up both printers.  Cut and paste what is shown as the** Driver:**

	HP Officejet 7300 Series, hpcups 3.12.6 (color, 2-sided printing)

There are actually several drivers that could be used for both printers, so you might want to define some duplicate printers with slightly different names and choose different drivers.  Also check that you are printing at High Quality and not Draft Mode or Fast Printing.

---

