---
title: "[SOLVED] Can't Print to HP2200 from Dapper"
date: 2007-05-15
forum: General Help
---

### Post by TennTux on 2007-05-15
I have configured 2 Linux Dapper Drake systems to print to an HPLaserJet 2200DN (Network) Printer. However I fail to print a test page from either one. However, a preveous dapper installation on one of the systems use to work. Also I am still able to dual boot and print from *that other operating system* so I know the printer still works.

I have tried removing and adding a printer with various options and have tried each of the following.
**HP JetDirect** verses **cups ipp**.
**Postcript (Standard Driver)** verses **LaserJet 2200 (hpijs - HPLJP 0.9.7) driver**.

The [JetDirect] + [HPLJP 0.8.7 driver] results in a status of **"Paused: /usr/lib/cups/backend/socket failed."**

The [cups ipp] + [Standard Postscript driver] results in a status of **"Printing: Printer busy: will retry in 10 seconds.."** (however the printer is not busy and it doesn't print after several minutes)

The [cups ipp] + [HPLJP 0.8.7 driver] results in a status of **"Printing: Printer busy; will retry in 10 seconds."**

The [JetDirect] + [Standard Postscript driver] results in a status of **"Paused: No %%BoundingBox: comment in header!"**

---

### Post by TennTux on 2007-05-15
Also since this is a network printer I can use a web-browser and goto the printer and see it's status so I believe I should be able to connect.

---

### Post by TennTux on 2007-05-16
Hi. Anybody have a clue??

---

### Post by jashore on 2008-02-12
Ok, I had a similar error with feisty/gusty.  After adding the printer (trying both the cups webmin and the System/Printing Gui)  I could send a test page to the Xerox Phaser 8550 printer, but could not print a webpage from firefox, pdf (from acroread), or print from command line.

In fact I **could** print a postscript page but not a png image which, I guess, means it  was a device driver problem.

Here's what I did:

1. I kept getting the same "Backend socket failed" (whatever) error on localhost:631
2. I also saw an error in /var/log/cups/error_log that said 'Unable to open PPD directory "/opt/share/ppd"'
3. Created /opt/share/ppd
4. chmod root:lp /opt/share/ppd
5. Download xerox linux drivers for printer from xerox support webpage
6. copy the relevant ppd files that I downloaded to /opt/share/ppd
7. Delete the printer using the cups webmin page (localhost:631)
8. Add a new printer using the System->Administration->Printing gui choosing the
    App/Jet Direct Printer option.
9. Specified the socket://your.printer.ip.here
10. Instead of loading the PPD file, chose "Xerox" from the device menu and low and behold it found the PPD files in /opt/share/ppd.  Chose the recommended driver and finished.

That seems to have worked.  Strangely, after I downloaded the PPD files, I could not get printing to work if I just "Browse"d for the PPD file when I tried to add the printer back using the Printing Gui.  The convoluted thing I did above was the only thing that worked.

---

### Post by TennTux on 2008-02-22
I finally figured out my problem. It turned out that when using "CUPS Printer (IPP)" the URI: needed to have more than just the IP address of the printer. I needed a URI like the following.

URI: [http://192.168.1.74/ipp/port1](http://192.168.1.74/ipp/port1)

Since I was not providing the ipp/port1 it was not working. :-O

---

