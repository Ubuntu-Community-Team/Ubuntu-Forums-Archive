---
title: "[SOLVED] Add/Remove Troubles"
date: 2007-12-03
forum: General Help
---

### Post by dstein on 2007-12-03
I used Add/Remove in Applications to install Octave. I then installed KOctave for a graphical environment. I did not realize that a whole bunch of KDE stuff would be installed along (I use Gnome). After seeing that Konqueror and a whole bunch of other programs in the 'Other' submenu had been installed, I tried uninstalling. To do this, I went back to Add/Remove and unchecked KOctave. This seems to have removed KOctave, but nothing that came along with it. How should I go about removing everything else (All that KDE stuff). Is there anyway to do this with apt-get. I would like to make sure that everything is removed. I believe that about 11 files were downloaded during the KOctave installation.

Thanks for the help.

---

### Post by zvacet on 2007-12-04
```
sudo apt-get remove --purge packagename
```

---

