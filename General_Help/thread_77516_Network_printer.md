---
title: "Network printer?"
date: 2005-10-16
forum: General Help
---

### Post by 4linux on 2005-10-16
I have a network printer (ethernet), and I can not seem to get it to work.  I have gotten it to work in a few other distros, which auto-detected it.  I am not sure exactly what to enter in the connection field of the printer setup.

(printer is a HP 5850)

Any ideas?

-Pat

---

### Post by wylfing on 2005-10-17
Try this:

1. Go into the printers control panel and choose Printer > Add Printer.
2. Select Network Printer and use the listbox to choose HP JetDirect.
3. In the Host box type the IP address of your printer.
4. Click Forward.

Any luck?

---

### Post by 4linux on 2005-10-17
:)  That did it.  

The test page says ghostscript, not CUPS...not sure what the difference is.   I'll try printing some various documents, web pages and graphics tommorow and see how it goes.

Thanks!

-Pat

---

### Post by hajk on 2005-10-17
I also have an HP DeskJet 5850 network printer -- it worked fine in Debian Sarge, but I have not been able to get it working properly in Ubuntu Breezy.
The configuration details are simple: HP JetDirect (actually IPP), static IP number of the printer, and port 9100; using the HP-DeskJet_5850-hpijs.ppd driver. 

In my case, the Ubuntu test page was shifted 2.5cm (1in) upwards, clipping the top of the page. And printing a PDF-file straight to the printer with
"lp file.pdf" puts the printer all of a sudden in double-sided mode -- even though I have it configured as single-sided.

I believe the problem is in the "gnome-cups-manager" package that is used via the Administration/Printing menu. May be it detects that the double-sided attachment is installed on the printer, and assumes that it then also should be used... In Debian Sarge I did the identical configuration via the [http://localhost:631](http://localhost:631) interface, but this route is disabled in Ubuntu. I have filed a bug about this -- #17820, so I am waiting for a solution on this.

---

### Post by 11hjpphty76lkjj on 2005-10-17
> **hajk]I also have an HP DeskJet 5850 network printer -- it worked fine in Debian Sarge, but I have not been able to get it working properly in Ubuntu Breezy.
The configuration details are simple: HP JetDirect (actually IPP), static IP number of the printer, and port 9100 said:**
> http://localhost:631[/url] interface, but this route is disabled in Ubuntu. I have filed a bug about this -- #17820, so I am waiting for a solution on this.

To access cups see this thread:

[http://ubuntuforums.org/showthread.php?t=73993](http://ubuntuforums.org/showthread.php?t=73993)

Also if you want full functionality of your printer try the HPLIP software:  [http://hpinkjet.sf.net](http://hpinkjet.sf.net)

Aaron

---

### Post by hajk on 2005-10-18
Thanks for the suggestion -- of course you meant editing /etc/cups/cupsd.conf... Sure, this gave me access to [http://localhost:631](http://localhost:631), I found the printer properly configured (except "A4" size had somehow reverted back to default "Letter" size), and the standard CUPS test page printed correctly in single-sided mode.

But still, my little PDF test file, produced with pdfLaTeX, prints double-sided when printed with "lp test.pdf", yet single-sided when printed from within Evince.
Curious...:confused:

---

### Post by tweaker on 2005-12-16
Thanks Wylfling thats just what the doctor ordered. I was having trouble with getting my old HP-T45 to hook up. Followed your instructions and BAM...gott'er done!

Thanks....;)

---

### Post by whittonm on 2008-05-17
Thanks.  Your post helped me too.

---

