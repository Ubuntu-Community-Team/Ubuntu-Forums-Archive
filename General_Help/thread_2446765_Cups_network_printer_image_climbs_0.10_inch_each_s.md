---
title: "Cups network printer image climbs 0.10 inch each successive page"
date: 2020-07-06
forum: General Help
---

### Post by j ferguson on 2020-07-06
Cups 2.2.7, Ubuntu 18.04, custom postscript ppd. 
Network printer, Sun SPARCprinter on SPARCstation 10, running GhostScript 6.01 under SunOS 4.1.4.

Amazingly this had worked since 2015.  but in 2018 after a move, the printed image on the SPARCstation rises about 0.10 inch every page, so that the image will start running off the top of the sheet in about 8 pages.

This does not happen for jobs printed to the ghostscript printer from the Sun SPARC station 10. It does not happen with print-files from the Ubuntu PC printed from the Sun. It only happens if I print through CUPS from the Ubuntu machine.

I've tried every imaginable modification in the PPD I'm using including changing filters, all sorts of modifications to image size, even adding 8 points to page height.  

So first questions: Can Cups do this?  Has anyone ever seen this before and if so, how was it caused? If you had the problem how did you fix it?

Is there a Cups command which I can put in the PPD which will either reset top of page on each subsequent page or let me subtract this over-run on each page?

---

