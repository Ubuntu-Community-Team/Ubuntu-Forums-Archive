---
title: "xdtv won't start - trying to convert VHS"
date: 2007-05-12
forum: General Help
---

### Post by summersab on 2007-05-12
Alright, my first question regards my errors with xdtv. I had it working perfectly on an Edgy setup a few months ago, but now on a Feisty setup, no go. I even tried a temporary Edgy setup. Grrr. The error I keep getting when running xdtv from the terminal is the following:

xdtv: error while loading shared libraries: libXaw3d.so.6: cannot open shared object file: No such file or directory

I have looked up what this file is and it appears to be part of libraries already included with Feisty. What is the deal here?

Second question - my intent is to digitize my old VHS tapes. xdtv has some pretty impressive deinterlacing features. However, does anyone suggest a better program? I would rather have my first question resolved first, but whatever. Thanks, community!

---

### Post by tariqf on 2007-09-20
I have same problem and also wanting to convert to vhs. did you solve the problem or find better software?

---

### Post by Den-Can on 2008-06-03
XDTV Installation ...

	1- Install XDTV from xdtv web site ( deb package )
	2- Install libxdtv from xdtv web site ( deb package )
	3- Need libXaw3d.so.6:   Parts in this package:   
           sudo apt-get install xaw3dg
	4- Install libzvbi.so.0 from repos  ( libzvbi in Synaptic )

Then open xdtv from the terminal or using Alacarte add this new application in your favorite menu section

( xdtv is in /usr/bin ... The Icons are in:/usr/share/xdtv/icons )

Note: To got XDTV menu rirgt click on your mouse 

Xdtv does not keep previous setting you got to edit xdtvrc in your home folder ( show hidden file first ) /home/yourname/xdtv ...

#
# Global options
#
norm = NTSC     ( or PAL or SECAM )
capture = grab
source = S-Video   ( you input source )
subpage = 888
freqtab = ntsc-us-cable

( more info at the bottom of this file )
Save the file and BINGO ... Hope this help ...

---

