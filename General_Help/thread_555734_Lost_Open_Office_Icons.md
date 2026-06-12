---
title: "Lost Open Office Icons"
date: 2007-09-20
forum: General Help
---

### Post by Ultra Magnus on 2007-09-20
Hi,

I decided to try out Lotus Symphony but decided to stick with open office but now all my .odt and .ods etc files have the Lotus symphony icons.

Is there any way I can get my OO.o icons back?

Thanks.

---

### Post by Jove on 2007-12-02
Been looking for an answer to this for ages - but fiddling around today I think I found it. Icons are in ~/.local/share/icons/hicolor/48x48/mimetypes so change these for the openoffice ones (in /usr/share/icons/hicolor/48x48/apps and bob's yer uncle. Worked for me, anyway

---

### Post by petsimbe on 2008-02-06
I had  same problem 
see  [http://ubuntuforums.org/showthread.php?t=632124](http://ubuntuforums.org/showthread.php?t=632124)

---

### Post by matt.fiscus on 2008-02-12
I tried out Symphony as well.  Here is how I got my OpenOffice.org icons back...

sudo apt-get install --reinstall hicolor-icon-theme

---

### Post by apetresc on 2008-02-12
Someone experiencing this should file a bug against Symphony. This is definitely not desirable behaviour, and should be easy enough to fix.

---

