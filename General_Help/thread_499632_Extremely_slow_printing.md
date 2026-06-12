---
title: "Extremely slow printing"
date: 2007-07-12
forum: General Help
---

### Post by kgator on 2007-07-12
I'm using a new install of 7.04 with an HP 882C printer. Test printing or printing from an application results in no action for several minutes, a short run of the print heads, then several minutes of nothing again. Ultimately I've never gotten a complete page out yet. Driver is Deskjet 882C hpijs. Printer is shown on LPT parport0 HPLIP. Computer is MSI K9N6SGM-V mobo, AMD X2 3800+ with 2 Gigs of ram. Same setup and driver has worked well in other distros. Any assistance in getting it to perform in Ubuntu would be greatly appreciated.

---

### Post by linuxwizard on 2007-07-13
According to this that printer should work perfect
[http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_882C](http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_882C)

Look over this an see if anything there that will help. Also a bug has been reported on LPT printers look at the bug report might show work around or fix.
[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)

---

### Post by condorloco on 2007-10-23
I have a very similar problem with my Kyocera FS-1030D after a clean install of 7.10. Especially pdf-Files need up to 10 minutes per page to print. With 7.04 everything was working fine. There are no error messages in the CUPS error log.

---

### Post by BobvanderPoel on 2007-11-02
I have the same problem with my HP-2550. However, following the fix from this page does fix it! Hope this helps.

[http://www.mail-archive.com/hplip-help@lists.sourceforge.net/msg03951.html](http://www.mail-archive.com/hplip-help@lists.sourceforge.net/msg03951.html)

---

### Post by rexless on 2007-11-05
I have an XP machine with a Samsung 1250 Laser attached.  The laser printer is shared via windows networking.  I have installed the printer to my notebook running Ubuntu 7.10.  It prints the pages fine, but it takes up to 10 minutes to do the job.

I was using CentOS 5 on a PC recently and was able to print to the same printer over the same network without this problem.

---

### Post by Locutuslaser on 2007-11-05
My deskjet 710 is also very slow. Will read & try the suggested solution. But i have another problem: even after correcting the offset of printerhead, it still makes fine white lines in the printed area. I cannot get it right. In win it was no problem, the offset must be corrected after a test page, you had to choose the right # from test and fill it in, then it was aligned.

---

### Post by icheyne on 2007-12-14
> **BobvanderPoel said:**
> I have the same problem with my HP-2550. However, following the fix from this page does fix it! Hope this helps.

[http://www.mail-archive.com/hplip-help@lists.sourceforge.net/msg03951.html](http://www.mail-archive.com/hplip-help@lists.sourceforge.net/msg03951.html)


Didn't work for my Deskjet 5940 as it was already set to io-mode=1.

:(

---

