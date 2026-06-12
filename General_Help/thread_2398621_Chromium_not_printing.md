---
title: "Chromium not printing"
date: 2018-08-15
forum: General Help
---

### Post by webmiester on 2018-08-15
Hi everyone,

I am using chromium for a browser-based kiosk system.  I am also using Ubuntu Mate 16.04 for both my PC setup and the RPi setup.  The Rpi setup is working fine, but the PC setup doesn't print.  

Here are some details:

My printer is an Epson m100. It is a network printer, although I have also plugged it in for USB on some of the RPis accessing it.  There is no  driver for the Epson m100 for the RPi, so I am using a different model and set it to monochrome (the m100 is a monochrome printer), and it works very well.  The PC version uses the Epson.ppd driver which, ubuntu recognizes as the one for the printer, and works too.  The system can also work using the same driver I use for the RPi.

Now here is the thing.  On the PC setup: The printer works when I use the "test printer" command from the printer administration page.  The printer works when I use it on libre office.  The printer DOESNT WORK on Chromium.  The error that comes up when I try printing is "Filter Failure".

I tried it both as (1)  directly connecting to the printer as a network printer, and (2) connecting to the RPi connected to it via USB, using thr RPi as a print server. In both instances I get the same results.  I've uninstalled and reinstalled ghostscript and cups, and I still get the same results afterwards.

Does anyone have any ideas on this problem?  I appreciate it very much.  Thank you.

---

