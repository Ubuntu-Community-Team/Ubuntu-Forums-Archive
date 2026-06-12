---
title: "Epson NX430 - Printed Colors Overlapping/Look Strange"
date: 2013-02-08
forum: General Help
---

### Post by mark2741 on 2013-02-08
Not sure how to describe it but basically whenever my Epson NX430 printer prints from Ubuntu, the colors are washed out and separated. I think what is happening/looks to be happening is that when a color is printed, instead of properly 'mixing' those two colors together what is happening is the individual color inkjets are printing one color and the other color(s) are offset from the first color, resulting in separate colors and a 3d-looking 'washed out' effect.

Anyone have this issue before? Printing in grayscale the printer works perfect. But color is horrible. I've tried switching to higher quality settings, changed it from RGB Color to CMYK, and other settings, to no avail.

I also just today downloaded and installed the latest deb package drive for the printer direct from Epson, but same issue.

---

### Post by Mark Phelps on 2013-02-09
I have installed Epson printers using CUPS -- and never had problems with printing.

To get to CUPS, open a browser and enter "localhost:631:" (without the quotes).  Once there see if you can add the Epson printer -- it will allow you to select a CUPS driver -- which in my experience, work quite well.

---

### Post by mark2741 on 2013-02-09
Thanks. I added the printer to the CUPS server and then did two print tests:

One from within the CUPS server pages via it's "Print a test page" feature. The other from within my browser - I simply printed an email from my Gmail account.

Same issue. Grayscale prints crisp and perfect. Color is horrible. I took a picture of the test page results, both grayscale and color printouts, so you can see:

[IMG]https://dl.dropbox.com/u/17209825/photo.JPG[/IMG]

---

### Post by NothingMuchHereToSay on 2013-02-09
I have this exact issue with my Epson NX330. Ubuntu 13.04 Beta.

---

### Post by mark2741 on 2013-02-09
It's surprising, considering Epson supports linux by offering a deb package for this very printer. Oh well. Have always had trouble with non-HP printers on linux. But HP printers always physically break on me within a couple of years of ownership so I now avoid them : (

---

