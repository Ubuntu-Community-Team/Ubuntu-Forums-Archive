---
title: "Minor apt problem."
date: 2005-11-02
forum: General Help
---

### Post by PhilR on 2005-11-02
I recently installed all the necessary multimedia gubbins as described in ubuntuguide, however I had a problem with the main repository for w32codecs not responding correctly. I've since installed the package from a different resository however as I originally Ctrl+C'd the first borked attempt it now attempts to fetch the package EVERY time I use apt-get. If I just Ctrl+C it it proceeds with the normal package setup but it means I get w32codecs errors every time I install something, which is pretty irritating.

If anyone could point me towards a way of getting rid of this I would appreciate it.

---

### Post by blu.gecko on 2005-11-02
yup yup, these codecs were removed, you will need to google them up. there is a package that debian uses, might do a debian package search.

[www.google.com/linux](www.google.com/linux) <------search here.

---

### Post by PhilR on 2005-11-02
I have the codecs, that isn't the problem. The problem is that apt tries to download them every time I run apt-get despite the fact that they are already installed.

---

### Post by PhilR on 2005-11-04
*bump*

Problems still exists. Anyone else have any idea?

---

### Post by felix_stegerman on 2005-11-04
Have you tried purging the package and reinstalling it ?

e.g.
# aptitude purge w32codecs
# aptitude install w32codecs
or if you installed w32codecs manually
# dpkg -i <w32-codecs-package>.deb

Maybe
# aptitude -f install
works too ? -f is meant to `fix' things.


Felix

---

### Post by PhilR on 2005-11-04
I think the problem is that the mplayer.hu site supposedly has an updated version of w32codecs to the one I actually have installed. So apt constantly tries to update the package but the site address does not work. I completly removed and re-installed w32codecs but the problem persists.

---

