---
title: "Printer Hangs with EVERYTHING!"
date: 2006-08-30
forum: General Help
---

### Post by mindseye1 on 2006-08-30
I was able to successfully install my USB printer, an HP PhotoSmart 7150, and Ubuntu automatically recognized everything along the way. Unfortunately though, when I go to print anything, including a test page, the printing will start and then almost immediately stop. I have about 20 sheets of paper here with only about the first 2 cm printed on them. It's not always in the same place either, I have one page that got about an inch and a half of printing!

I always ending up having to cancel the job and then restart the printer to get things back up and ready to try again. Has anyone else experienced this, or does anyone have any solutions? Thanks for the help!

---

### Post by mindseye1 on 2006-08-31
Just wanted to add that this printing issue also occurs when printing over the network from a WinXP machine.

Also, if I boot the Ubuntu machine back into WinXP, printing works fine (so it can't be a hardware issue).

---

### Post by slimdog360 on 2006-08-31
I was going to say this is a driver problem (which it probably is) but the networking in windows thing threw me a bit. Id recommend trying a few different drivers and se what happens. Here is a few
[http://http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7150]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7150")

---

### Post by mindseye1 on 2006-08-31
Well I tried the hpijs-rss driver, but got the same results. I will try the gutenprint driver next. Thanks for the help!

Edit: Tried that too, no good. Is there any chance it could be a USB driver problem?

---

### Post by mindseye1 on 2006-09-01
Anyone have any ideas on what I could try?

---

### Post by mindseye1 on 2006-09-04
Got any printer gurus out there?

---

### Post by patrickfromspain on 2006-09-04
go to cups.org and download the latest stable release and compile it (it's really simple, just ./configure && make && sudo make install

I had the same problem using turboprint drivers and compiling cups 1.2.1 from the official cups site worked :)

---

### Post by lcampagn on 2006-09-14
I have the same problem with an HP DeskJet 882c. The problem occurs mainly while printing PDFs (though admittedly I haven't tried printing much else). Generally, if I print via the KDE printing system or by issuing "lp somefile.pdf" on the command line, the printer starts the first 2cm of the page, hangs for about 10-15 seconds, then feeds the page out and prints the first 2cm of the next page, and so on.

However: if I print using gpdf, everything works fine, which leads me to believe that something in the PDF is hanging up CUPS, and gpdf is doing some processing that removes the problem.

I have tried looking for error messages in the CUPS logs (even after bumping the loglevel up to debug), with no luck. I have also checked the spooled files for problems, and they seem to be ok..

---

### Post by mindseye1 on 2006-11-13
> **patrickfromspain said:**
> go to cups.org and download the latest stable release and compile it (it's really simple, just ./configure && make && sudo make install

I had the same problem using turboprint drivers and compiling cups 1.2.1 from the official cups site worked :)

I'm trying to keep the system completely package based, I'd rather not compile my own stuff. I recently upgraded to Edgy in hopes that the problem would go away. I've actually had a few times where a whole item will print, but the printer still hangs very often. Guess I just have to wait until Fiesty to try again.

---

### Post by SendDerek on 2006-12-07
I would like to revise this thread back from the dead.  Sorry if this is a problem.

I've recently been having this exact same problem over my network printer (HP PSC 1210).  It just started yesturday and I usually didn't have any problems before.  It seemed that I had the most problems printing from OpenOffice because the printer would always pause, but it didn't with other programs that I tried.

Also, I'm noticing that a simple word document that I'm trying to print from Opera is showing like this in the print queue in windows xp: Remote Downlevel Document  Printing  Guest  52.1KB/3.98MB it hasn't budged in the last 10 minutes.

As a side note, somebody had recommended to enable the bidirectional support to be able to print through a SAMBA shared printer and it worked really well for a while.

I'm going to try the latest CUPS driver (v1.2.7) and see what happens.

---

### Post by SendDerek on 2006-12-09
Unfortunatly, the new CUPS driver didn't seem to correct the issue.

The printer even hangs on the test page print from the printer manager.

Any suggestions?  Is it going to be a setting on the Windows computer or is it a problem on my machine?

It seems that whenever I print even a simple document (like the test page) the size of the print goes to about 7.00MB, and it always stops around 52KB.

---

### Post by budgie9 on 2006-12-09
I would like to throw this in to this post.
In the days when we used only serial or parallel cables this sort of problem occured frequently.
I recall having the same situation arise with Amiga, QL and even some of the early PC's.
It was simply that the cable was too long for the computer driver to push the data through, 

Though I have to admit I am old fashion and still prefer a parallel cable driven printer and have little experience with USB only printers, so I would not know if this is the actual cause.

This may be worth nothing. however try a shorter USB cable. 
Could be worth looking at?

Another thought came to mind. It would seem to me going by the size of the file, that the LF (Line Feed) commands are being added to the file itself, increasing the size of the file thus leaving added blank lines. That may indicate that the program(s) are not accessing the driver correctly. Instead simply pushing out LF lines. perhpas in an attemp to see the driver. Can I further sugggest you try one of the other drivers in the HP range. They may not print correctly, but you may see some other changes that may help to resolve your problem.

David.

---

### Post by pieroxy on 2007-01-07
I have a quite similar problem. I have an EPSON stylus photo 870 and printing is fine but for big stuff - pictures printed with high quality. Everything else is fine, but photos would print for a few seconds and then would stall.

I must say I had this problem with Windows and the knowledge base at epson diagnosed it as a driver's bug. You just disable the buffer caching and everything works fine. It was mentionned issues related to timing on the USB port. Of course, Linux is not supported...

Anyways, I fixed my issue by plugging my printer directly in one of the PC's USB port, not on a hub (powered or not). In fact, the printer's user's manual recommend this setting as well.

Dunno if that'll help you or not. Cheers.

Note: My fix is recent, so it might not work a 100% (I will see as time goes) so if someone has another fix, let us know!)

---

