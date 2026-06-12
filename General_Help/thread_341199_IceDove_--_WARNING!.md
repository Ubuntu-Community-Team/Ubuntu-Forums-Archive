---
title: "IceDove -- WARNING!"
date: 2007-01-18
forum: General Help
---

### Post by gjtoth on 2007-01-18
I don't know if this will happen on your system.  I don't even know how it TRULY affected mine yet.  B U T... I went to install the IceDove .deb file and it came up broken because it lacked libfontconfig1.  No big deal, right?  Well, it seems it broke the index.  So, I try sudo apt-get install -f with no joy.  Then, I tried sudo aptitude install -f and it fixed it however, it removed a TON of lib files, Abiword, Exaile and God knows what else.  I've tried to reinstall Exaile to no avail.  Haven't tried Abiword.  I tried to install something else and it claimed it couldn't find the Gnome library(s)!  But, my index is fixed.  ](*,)

---

### Post by gjtoth on 2007-01-20
I'm starting to find how this has affected my system.  So far, Open Office was almost halfway removed.  The only thing left was the word processor portion (I had the entire suite installed along with all the available plug-ins) and even the WP was screwed up.  So, I had to reinstall everything pertaining to OO.  I had some plug-ins for Thunar File manage that miraculously disappeared in the "fixing" process, too.

I'm sure they will be more.

---

