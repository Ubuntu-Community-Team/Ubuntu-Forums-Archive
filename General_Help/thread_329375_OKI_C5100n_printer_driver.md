---
title: "OKI C5100n printer driver"
date: 2007-01-01
forum: General Help
---

### Post by kinemagician on 2007-01-01
Does anybody know where I can get the drivers for this printer?

[http://www.linuxprinting.org/printer_list.cgi?make=Okidata](http://www.linuxprinting.org/printer_list.cgi?make=Okidata)

says that this printer cannot simply be used under Linux !??

---

### Post by evilpenguin on 2007-11-02
They are not lying to you. This printer is a "winprinter" (meaning it uses Windows' GDI code to render images in its Windows driver, not in the printer firmware). Basically, the printer isn't smart enough to print.

I have one of these printers and I can print to it from Linux, but to do it I have to have a Windows box with the driver installed. I then set up a "Windows Printer Port" that pretends to be a Postscript printer. This port uses Ghostscript and redmon to render the Postscript and then print it to the Windows-hosted C5100 printer. I then share the "fake" printer and configure Linux to use it as a Samba-shared Postscript printer.

This URL gives the basics on setting up such an environment on a Windows box. At one time I even hosted the "Windows box" on VMWare on my Linux box, but I finally gave up and put a cheap Windows box on my network just to use my color laser printer.

[http://geekinfo.net/article.php?story=20030209135156781](http://geekinfo.net/article.php?story=20030209135156781)

Basically, I would return (or better, not buy) any "winprinter," but the C5100 family is by far the nicest color laser printer for the price. Postscript supporting color laser printers are ruinously expensive. I would never do this for some dumb old inkjet.

Believe me, I feel your pain.

Oh, and I upgraded to Vista, this quit working, so I downgraded back to XP. I don't actually use Windows for much (unless a client forces me to develop in C#.NET), so I didn't bother to find out why it broke.

Good luck!

---

### Post by weller on 2008-02-04
Hi!

These printers use the hiperc protocol for sending the data to the printer.

Look at a first alpha driver at [http://foo2hiperc.rkkda.com/](http://foo2hiperc.rkkda.com/) and please don't forget to support Rick with the further development :-)


Regards,
  Andreas Weller

---

