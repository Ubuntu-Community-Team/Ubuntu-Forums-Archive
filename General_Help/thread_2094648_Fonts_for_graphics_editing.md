---
title: "Fonts for graphics editing"
date: 2012-12-14
forum: General Help
---

### Post by satimis on 2012-12-14
Hi all,

Ubuntu 12.04 desktop 64bit

I expect installing some fonts for graphic editing.

$ apt-cache search fonts | grep ttf
found me many.

Where can I find their examples before installing them.  It is not feasible installing all of them.  Please help.

TIA

B.R.
satimis

---

### Post by Frogs Hair on 2012-12-14
I have used this before.  [http://www.myfonts.com/WhatTheFont/](http://www.myfonts.com/WhatTheFont/)

Additional fonts with sample.  [http://www.urbanfonts.com/](http://www.urbanfonts.com/)

---

### Post by satimis on 2012-12-14
> **Frogs Hair said:**
> I have used this before.  [http://www.myfonts.com/WhatTheFont/](http://www.myfonts.com/WhatTheFont/)

Additional fonts with sample.  [http://www.urbanfonts.com/](http://www.urbanfonts.com/)
Thanks for your advice.

But I have to download them treating the fonts as graphic and using graphic software to edit them.  Are there similar fonts on repo for installation?  I can type the characters on document.

B.R.
satimis

---

### Post by Frogs Hair on 2012-12-14
> using graphic software to edit them What software ? I use gimp and have added text to computer wallpaper from the installed font list. I have overlaid/ layered text from different sources.

---

### Post by satimis on 2012-12-14
> **Frogs Hair said:**
> What software ? I use gimp and have added text to computer wallpaper from the installed font list. I have overlaid/ layered text from different sources.
I have done lot of graphic editng in the past, about 10 years ago, running PhotoShop and then GIMP.  Actually I need the fonts for html editing avoiding graphic editing, if possible, to save time.

B.R.
satimis

---

### Post by Frogs Hair on 2012-12-14
The software center offers Fontforge but I know nothing about the program. 

I get a number search of results for HTML font editor on Google also see Bluefish in the software center.

---

### Post by grahammechanical on 2012-12-14
I may be wrong. In my ignorance I am sometimes completely wrong.

Your search using apt-cache search has found you a list of ttf fonts available for download using apt-get, Synaptic Package Manager. I think that the command apt-cache search is searching for the text string 'ttf' in all the scripts that the apt-cache knows about. 

Font Viewer and File Manager directed to /usr/share/fonts/trutype will show us examples of fonts installed on the system. You are looking for examples of fonts that may not yet be installed. I am not sure that is possible.

Regards.

---

### Post by satimis on 2012-12-15
Hi,

> **grahammechanical said:**
> 
Your search using apt-cache search has found you a list of ttf fonts available for download using apt-get, Synaptic Package Manager. I think that the command apt-cache search is searching for the text string 'ttf' in all the scripts that the apt-cache knows about. 

Whether you meant;

$ apt-cache search synaptic | grep synaptic```

xserver-xorg-input-synaptics - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-synaptics-dev - Synaptics TouchPad driver for X.Org server (development headers)
gsynaptics - configuration tool for pointing devices (transitional package)
synaptic - Graphical package manager

```

synaptic - Graphical package manager ?

> 
Font Viewer and File Manager directed to /usr/share/fonts/trutype will show us examples of fonts installed on the system. You are looking for examples of fonts that may not yet be installed. I am not sure that is possible.

Font Viewer

$ apt-cache search 'Font Viewer'```

gnome-font-viewer - font viewer for GNOME

```

$ apt-cache policy gnome-font-viewer```

gnome-font-viewer:
  Installed: 3.4.0-1
  Candidate: 3.4.0-1
  Version table:
 *** 3.4.0-1 0
        500 http://hk.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

```

$ which gnome-font-viewer```

/usr/bin/gnome-font-viewer

```
But I couldn't start it on terminal.

$ apt-cache search 'Font Manager'```

defoma - Debian Font Manager -- automatic font configuration framework
defoma-doc - Debian Font Manager documentation
font-manager - font management application for the GNOME desktop
fontmatrix - featureful personal font manager
psfontmgr - PostScript font manager -- part of Defoma, Debian Font Manager

```
There are several

Edit
====

font-manager is the package which I need.  It is now running.  Wonder!!!  It allows me to view all installed fonts.  

Advanced Font Manager for Ubuntu &#8211; &#8220;Font-Manager&#8221;
[http://www.hecticgeek.com/2011/10/advanced-font-manager-for-ubuntu-font-manager/](http://www.hecticgeek.com/2011/10/advanced-font-manager-for-ubuntu-font-manager/)

Thanks


B.R.
satimis

---

### Post by satimis on 2012-12-15
> **Frogs Hair said:**
> The software center offers Fontforge but I know nothing about the program. 
Hi,

FontForge 
[http://fontforge.org/](http://fontforge.org/)
An outline font editor that lets you create your own postscript, truetype, opentype, cid-keyed, multi-master, cff, svg and bitmap (bdf, FON, NFNT) fonts, or edit existing ones.....

> 
I get a number search of results for HTML font editor on Google also see Bluefish in the software center.
Bluefish is a GUI webpage editor

Thanks

satimis

---

### Post by sumon1234 on 2013-07-15
Hi all,
I hope you will install some fonts for graphics.

Download too easy for you in this site.

You get Free Fonts for Windows and Macintosh.

**[click here]("http://www.fontsbucket.com/")**


PPI
Stars

---

