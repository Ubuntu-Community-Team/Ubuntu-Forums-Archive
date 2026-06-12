---
title: "HP 5550dn Printer never stops printing"
date: 2013-07-10
forum: General Help
---

### Post by g9164315 on 2013-07-10
Hi all, 

I got the clue from here --> [http://h30499.www3.hp.com/t5/Printers-LaserJet/Network-Printer-new-will-not-stop-printing-P2035n/td-p/2369577#.Ud6GReHI_CI](http://h30499.www3.hp.com/t5/Printers-LaserJet/Network-Printer-new-will-not-stop-printing-P2035n/td-p/2369577#.Ud6GReHI_CI)

Same condition!!!! It even happens in Window 7!!!!

And someone provides the solution,**"UNcheck "bidirectional support"**.

Unfortunately, no way to disable bidirectional support in CUPS.

Does anyone know how to do?



==============================================================================================


Last year, I installed ubuntu 12.10 and the printer is HP 5550dn (hplip was also installed). During this period, I have upgraded many packages. Recently, I need to print a ducument and discover that HP 5550dn always print the first page and never stop. It just "**keep printing**". The last version for hplip was also installed, but it can't solve the problem. After removing hplip, the condition also happened. The printer is connected via network. System information are provided below lines:


kernel-release: 3.8.0-26-generic
kernel-version: #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013

driver: postscri.ppd 1.1 (from test page)

+++-======================-================-================-=================================================
ii  bluez-cups             4.101-0ubuntu8b1 amd64            Bluetooth printer driver for CUPS
ii  cups                   1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - server
ii  cups-browsed           1.0.34-0ubuntu1. amd64            OpenPrinting CUPS Filters - cups-browsed
ii  cups-bsd               1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - BSD commands
ii  cups-client            1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - client programs
ii  cups-common            1.6.2-1ubuntu5   all              Common UNIX Printing System(tm) - common files
ii  cups-daemon            1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - daemon
un  cups-driver-gutenprint <&#28961;>                             &#65288;&#28961;&#30456;&#38364;&#20171;&#32057;&#65289;
ii  cups-filters           1.0.34-0ubuntu1. amd64            OpenPrinting CUPS Filters
ii  cups-pdf               2.6.1-8          amd64            PDF writer backend for CUPS
ii  cups-pk-helper         0.2.4-0ubuntu5   amd64            PolicyKit helper to configure cups with fine-grai
ii  cups-ppdc              1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - PPD manipulatio
un  cupsomatic-ppd         <&#28961;>                             &#65288;&#28961;&#30456;&#38364;&#20171;&#32057;&#65289;
ii  ghostscript-cups       9.07~dfsg2-0ubun amd64            interpreter for the PostScript language and for P
un  hplip-cups             <&#28961;>                             &#65288;&#28961;&#30456;&#38364;&#20171;&#32057;&#65289;
ii  libcups2:amd64         1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - Core library
ii  libcups2:i386          1.6.2-1ubuntu5   i386             Common UNIX Printing System(tm) - Core library
ii  libcups2-dev           1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - Development fil
ii  libcupscgi1:amd64      1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - CGI library
ii  libcupsfilters-dev     1.0.34-0ubuntu1. amd64            OpenPrinting CUPS Filters - Development files for
ii  libcupsfilters1:amd64  1.0.34-0ubuntu1. amd64            OpenPrinting CUPS Filters - Shared library
ii  libcupsfilters1:i386   1.0.34-0ubuntu1. i386             OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2:amd64    1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - Raster image li
ii  libcupsimage2:i386     1.6.2-1ubuntu5   i386             Common UNIX Printing System(tm) - Raster image li
ii  libcupsimage2-dev      1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - Development fil
ii  libcupsmime1:amd64     1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1:amd64     1.6.2-1ubuntu5   amd64            Common UNIX Printing System(tm) - PPD manipulatio
un  printer-driver-hpcups  <&#28961;>                             &#65288;&#28961;&#30456;&#38364;&#20171;&#32057;&#65289;
ii  python-cups            1.9.62-0ubuntu3  amd64            Python bindings for CUPS
ii  python-cupshelpers     1.3.12+20130308- all              Python modules for printer configuration with CUP
un  python2.7-cups         <&#28961;>                             &#65288;&#28961;&#30456;&#38364;&#20171;&#32057;&#65289;


Does anyone have any suggestions?

---

