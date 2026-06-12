---
title: "Cannot open an eps file in Lubuntu - I can open these files in Ubuntu - help"
date: 2015-08-21
forum: General Help
---

### Post by wg-2 on 2015-08-21
I recently installed Lubuntu 15.04 and can no longer open EPS files.  My prior system  (Ubuntu 12.04) had no problem allowing me to work with EPS files.  There were many software packages that use to read these files including, PDF readers, GIMP, Inkscape and more.  With Lubuntu none of these packages allow access.

Is this a problem with 15.04?

thanks,
wayne

---

### Post by aeden.d on 2015-08-24
I'm assuming by "PDF readers" you have already tried evince? Evince should be included with your Lubuntu install. Lubuntu has access to Ubuntu's repos, so you could try installing **gv**, it uses the ghostscript PostScript interpreter so it *should* open the eps file. You can install gv with **sudo apt-get install gv** The developers webpage for gv is [here]("http://www.gnu.org/software/gv/")

I didn't see any bug reports for eps files in Lubuntu. You can check [https://bugs.launchpad.net/lubuntu](https://bugs.launchpad.net/lubuntu) and search for something related or file a bug if you feel the need.

---

### Post by steeldriver on 2015-08-24
What do you mean exactly by "none of these packages allow access" - what actual error message / behavior are you observing?

The default evince viewer is working for eps files on 15.04 for me, under an xfce4 desktop

---

