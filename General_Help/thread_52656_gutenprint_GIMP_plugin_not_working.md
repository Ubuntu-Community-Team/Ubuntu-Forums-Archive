---
title: "gutenprint: GIMP plugin not working"
date: 2005-07-28
forum: General Help
---

### Post by cwolt on 2005-07-28
I'm looking for some advice on getting the new version of gimp-print (called gutenprint now) to work with the GIMP.

And I'm very new to Linux, so I may have done something simple wrong without realizing it!

Here's the problem:  I decided to try to install gutenprint so that I could use a new printer, an Epson R800, to print photos.  It installed fine (on the second try), and most features seem to work perfectly, but the GIMP print plugin has problems:

1. When the print dialog box opens, it doesn't list printers already set up using the System>Administration>Printing.  It does, though, allow me to add a new printer and set it up, and I can then print.
2.  Most important:  the dialog does not list many important controls--resolution, dither algorithms, many of the color control options.  I did check all of the panels, and the options simply are not there.  (All these controls are, by the way, available when I access the printer through System>Administration>Printing)
3.  If I close the GIMP print dialog box, and then open it up again, the printer that I added and set up before is now gone.

Here's what I did to get to where I am:
I first tried installing the gutenprint 5.0 beta-4 release from [http://sourceforge.net/projects/gimp-print/](http://sourceforge.net/projects/gimp-print/).  I tried to first install all of the necessary packages mentioned in the documentation.  Gutenprint would configure, but "make" produced errors.  I then used "make distclean" (was this the right thing to do?) and then deleted the source files.

Next, I found a version of gutenprint at [http://packages.debian.org/unstable/source/gutenprint](http://packages.debian.org/unstable/source/gutenprint).  I made sure all of the dependencies listed on that page were installed, and then installed gutenprint.  It seemed to work fine, but I ended up with the problems described above.

Any insights would be greatly appreciated!

---

