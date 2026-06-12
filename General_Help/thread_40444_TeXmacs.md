---
title: "TeXmacs"
date: 2005-06-09
forum: General Help
---

### Post by larry on 2005-06-09
I often use TeXmacs as a graphical interface to Maxima, in order to do some scintific computing.
I notice that TexMacs is deadly slow on my machine (athlon amd 900).
Is it because of my hardware? 
If I use Maxima from the command line, it is much faster so I think that TeXmacs is the problem.
I am a newbie; I do not know exactly how to deal with it and if there is anything I can do.
I do not know which graphic card I have, Ubuntu worked out of the box; i tried installing some nvidia drivers, but I did not notice any improvement.
Sometimes Texmacs crashes and the whole desktop freezes...I have never had this problem with any other application.
Anybody can help?
Cheers
Larry

---

### Post by ow50 on 2005-06-09
Try [wxMaxima](http://wxmaxima.sourceforge.net/).

---

### Post by larry on 2005-06-10
Ok, that should help. Last question (I am a newbie): how do I install the deb file? Do I need to download it to a specific directory? And what about eventual updates in the future (how can I install a newer version when it is released)?
Cheers
Larry

---

### Post by tread on 2005-06-10
If you downloaded the .deb file, just install it using 

sudo dpkg -i filename.deb

When you get the updated version, just do the same.

---

### Post by larry on 2005-06-10
So it was as easy as that! Wxmaxima looks much more responsive than TexMacs!
Cheers
Larry

---

### Post by ow50 on 2005-06-14
[Sorry to continue this on a tread titled TeXmacs, but anyway...]

The deb linked on wxMaxima website is compiled against wx 2.4, which probably means it's gtk1. I contacted the debianizer and got him to upload the full debian sources and I built a deb out of that for hoary. I built it agaist wx 2.5, so it's gtk2. The versions of two of the dependency packages are available from backports.

Package:
[wxmaxima_0.6.1-2_i386.deb](http://koti.mbnet.fi/ots/linux/hoary/wxmaxima_0.6.1-2_i386.deb)

Source:
[http://softwarelibre.uca.es/debian/](http://softwarelibre.uca.es/debian/)

---

