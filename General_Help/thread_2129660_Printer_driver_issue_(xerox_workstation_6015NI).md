---
title: "Printer driver issue (xerox workstation 6015NI)"
date: 2013-03-26
forum: General Help
---

### Post by Dude Random21 on 2013-03-26
Well this is my first time posting, I've used this site before multiple times for information (great forum btw) but this time I'm really stumped.

So here's the issue: I bought a Xerox workstation 6015NI which was a bit of a rushed purchase because I didn't do my usual pre purchase research for compatibility. Now that I have it however I learned that the colours are messed up when using any ubuntu version above 11.10 (I'm running 12.04). Now I have multiple computers in my household (linux, mac and windows) so with my previous printer I had a print server (cups and samba) going on my main computer (ubuntu 12.04 amd64). My goal is just to pass everything back through that print server so I need to get that computer working with the printer. The original driver provided by xerox did not support amd64 so I found a way to make it work by using the RPM linux version [here]("http://linuxliberations.blogspot.ca/2012/08/printing-with-xerox-workcentre-6015ni.html").

Now the colour issue still precisest but to be sure that my fix for the amd64 is not the cause for any issues I'm using my computer running i386 for testing. I found that by using the [foo2hbpl driver]("http://foo2hbpl.rkkda.com/") I'm supposed to get my colours back correct. I tried installing this driver, no success, then noticed that I was missing the ghostscript it basses itself on so I installed that (from source) then still no success. I found in the install file that for the driver to work I needed version 8.54 to 8.7x of ghostscript so I tried uninstalling the ghostscript (make uninstall) but obviously this is not supported by ghostscript -.-' so I need to go look for the files and delete them manually. Since I figure that I'll be reinstalling just with a previous version I can just delete the actual executable and go from there so I identified it and deleted it. Now while doing the ./configure step for the 8.54 version I get "Error 1" (will provide a full error log upon request) and now I'm just really at a loss of what to do... Has anyone else used this or a similar driver before??

Any help at all will be received with great appreciation!

---

