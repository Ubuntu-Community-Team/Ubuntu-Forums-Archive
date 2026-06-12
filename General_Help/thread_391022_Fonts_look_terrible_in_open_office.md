---
title: "Fonts look terrible in open office"
date: 2007-03-22
forum: General Help
---

### Post by Plato on 2007-03-22
I run linux mint. I have installed KDE desktop recently and some strange things happened with font rendering. I have set antialising and dpi in KDE and overall look improved, but as I opened open office I was disappointed - the fonts there looked really bad. I have tweaked my system in many ways but nothing helps. The strange thing is that it caused the same effects in Gnome - better look in general but crap in open office. I removed KDE and still have bad fonts in office application.
Has anybody any idea how to improve the situation?

---

### Post by thingy on 2007-03-22
If you don't have the MS Truetype fonts installed, then OO.org is prob. using the crappy fixed width ones or the Adobe TYPE 1 fonts.

Follow this guide for installing the MS fonts:

[http://www.hauntedpalace.net/kingdom/geekery-howtos/msfonts-ubuntu/](http://www.hauntedpalace.net/kingdom/geekery-howtos/msfonts-ubuntu/)

Or follow this one:

[http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)
[COLOR=#800080][/COLOR]

---

### Post by Plato on 2007-03-23
I already have installed the true type fonts, so that obviously is not a problem.

---

### Post by mat_london on 2007-03-23
Yes they do look terrible.

I fixed it by running the latest snapshot from here.

[http://update.services.openoffice.org/ooo/snapshot.html](http://update.services.openoffice.org/ooo/snapshot.html)

Extract the rpms to a folder and use alien to turn them all into debs.

Search the forums here for how to turn a folder into a repository.

Turn your folder full of new ooffice debs into a repo and install.

This gives me great fonts in ooffice.

Mat

---

### Post by Plato on 2007-03-23
Thanks Mat! I'll try that. However it does not sound that simple.

---

### Post by thingy on 2007-03-23
> **Plato said:**
> Thanks Mat! I'll try that. However it does not sound that simple.

Can you post a screenshot of the whole desktop with openoffice.org running on it.

---

### Post by diceratops on 2007-04-21
Very nice directions for reinstalling Open Office are given at:

[http://ubuntuforums.org/showthread.php?t=398074](http://ubuntuforums.org/showthread.php?t=398074)

Although it is written for Edgy, I was able to complete it just fine in Feisty. A word of caution: I received some error messages when pasting the block of commands into the terminal. Instead, I recommend going through command by command.

Hope this helps!

Andy

---

