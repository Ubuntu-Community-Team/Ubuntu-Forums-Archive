---
title: "Firefox, KPDF, Ubuntu"
date: 2007-11-07
forum: General Help
---

### Post by oliso on 2007-11-07
I want to install Ubuntu 6.08 - 7.10 (don't care) on 132 laptops. The only application I need is Firefox and a good pdf plugin for in-line display of pdf documents. Adobe Reader will not work due to lockups in Firefox.

I've successfully tested the Firefox KPDF plugin in KDE using PCLinuxOS, but the KDE desktop has cursor control problems with my touch pads. I suspect the same problem exists in Kubuntu. I don't know for sure, but could not test it because I can't figure out how to install the KPDF plugin in Kubuntu.

Is there a way to install the KPDF Firefox plugin (and the necessary KDE libraries) in an Ubuntu distribution using Gnome? That would be the ideal solution.

Thanks!!!

---

### Post by oliso on 2007-11-07
I've just finished testing cursor control with Kubuntu. It is ok. That means I could use Kubuntu if I can get the PPDF plugin for Firefox installed.

---

### Post by tubasoldier on 2007-11-07
KPDF for firefox in ubuntu is very simple. Just install KDPF and mozplugger. In a terminal type:
```
sudo apt-get install kpdf mozplugger
```

There you have it

---

### Post by oliso on 2007-11-07
I installed KPDF in Ubuntu via apt-get. It installed and runs. Unfortunately, it has serious and strange problems opening pdfs. More freqently than not, it just freezes at loading. When it does work, it's great. It is also very slow to launch. I think I'll try Kubuntu before giving up on the KPDF solution.

I'm guessing there is a way to get the plugin to work there, as well.

Thanks!

---

### Post by tubasoldier on 2007-11-07
The way to get the plugin to work with Kubuntu is the same as I explained. I use KPDF exclusively. Three years ago I would not have touched it. Now it works really well and is lightweight. Acrobat Reader is a very heavy application just to look at a PDF file.

---

### Post by oliso on 2007-11-08
KPDF works great in Kubuntu. I think this will do nicely.

I am going to play with it again in Ubuntu today, but I'm good to go in any case.

Thanks for the help!

---

### Post by boob11 on 2008-01-06
[PHP]http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fk%2Fkdegraphics%2Fkpdf_3.5.8-0ubuntu1_i386.deb&md5sum=3415fe6a94e7a01a1478de2349052cb4&arch=i386&type=main[/PHP]

---

