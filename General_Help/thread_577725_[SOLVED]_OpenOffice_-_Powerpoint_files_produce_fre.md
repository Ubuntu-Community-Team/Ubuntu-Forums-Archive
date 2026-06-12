---
title: "[SOLVED] OpenOffice - Powerpoint files produce freeze..."
date: 2007-10-16
forum: General Help
---

### Post by perixx on 2007-10-16
I got the problem, that OpenOffice opens my Office 2000 documents, except Powerpoint files like .pps and .ppt - 

opening them will work, but as soon as I start the presentation, the whole desktop freezes. Only Alt+F4 can recover the desktop or Ctrl + Alt + Backspace to close Xserver helps....


perixx

---

### Post by perixx on 2007-10-31
Allright, I got it done!


Now I did the following, analog to the information on OO-forums - I completely removed the old OO version with Synaptic, closed it again and then:

1) downloaded the localized archive, linked on suggested site
[http://download.openoffice.org/index.html](http://download.openoffice.org/index.html)

2) used Xarchive to unpack it to the new directory /home/USER/tmp

3) opened a Terminal in that directory and typed
sudo dpkg -i *.deb

Finished


P.S.: this was pretty obviously caused by bad Ubuntu-OpenOffice packages from the official repositories. Many similar OpenOffice-issues have been reported in the OpenOffice community forums and are very likely avoidable by completely replacing most especially this particular OO-Ubuntu-version by the official Debian package. 


perixx

---

