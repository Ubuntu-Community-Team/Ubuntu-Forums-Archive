---
title: "Remove desktop environment but keep gorgeous fonts"
date: 2014-10-07
forum: General Help
---

### Post by nathanvy on 2014-10-07
Hello,

I switched from Debian due mostly to hideous fonts.  I spent 4+ hours trying to get fonts in Debian to look as nice as they do in ubuntu, but no luck, so here I am.

What I would like to do is:
[LIST]
[*]Remove my DE (gnome) entirely, including gdm
[*]install awesome wm and SLiM
[*]Still have gorgeous fonts
[/LIST]

What package(s) and configs do I need to keep in order to do this?

Thanks
N

---

### Post by T.J. on 2014-10-07
Just so you know, Debian and Ubuntu use almost identical font installs.  In fact, Ubuntu is just a copy of Debian with extra things added.

To answer your question, that depends on what fonts you like.  Not every DE can read the newer style font files, either do to age, or simply the developer who wrote the DE not adding support.  Generally speaking, fonts should not be part of any particular DE, and should be available regardless of which you use.  The majority of font problems in applications on LCD/LED screens comes from the fact that some fonts use bitmaps rather than proper anti-aliasing.  Sometimes you can fix that by editing your personal font settings  on .fonts.conf in your home folder: 

<match target=”font” >
<edit name=”embeddedbitmap” mode=”assign”>
<bool>false</bool>
</edit>
</match>

---

### Post by nathanvy on 2014-10-07
> **T.J. said:**
> Just so you know, Debian and Ubuntu use almost identical font installs.  In fact, Ubuntu is just a copy of Debian with extra things added.I know that Ubuntu is based on Debian.  But, my experience has been that the difference between font rendering quality in a default Debian install and fonts in a default ubuntu install is like night and day.  I tried a ****-ton of tweaks and configs and whatnot.

> To answer your question, that depends on what fonts you like.  Not every DE can read the newer style font files, either do to age, or simply the developer who wrote the DE not adding support.  Generally speaking, fonts should not be part of any particular DE, and should be available regardless of which you use.I think maybe I wasn't clear.  I'm going to be removing the DE entirely and just using a wm.  I know that fonts aren't part of the DE but I'm sure there's some particular package (cairo, perhaps?  fontconfig?) that I need to keep in order to keep the same font rendering behaviour as I have right now.

I just want to find out if, for example, removing "ubuntu-gnome-desktop" will remove those packages.

---

### Post by T.J. on 2014-10-07
To answer your question directly, I do not know.  That depends on how Canonical setup the package dependency chains.  It also depends on what support was compiled into the wm.  I do not use Ubuntu any longer, so I can't be more specific.  I wouldn't think so, and if it does you can always re-install Cairo.  It would help if you told me what wm you had in mind.

Just a thought.  Sometimes you can fix ugly fonts by editing font settings in .fonts.conf in your home folder: 

<match target=”font” >
<edit name=”embeddedbitmap” mode=”assign”>
<bool>false</bool>
</edit>
</match>

---

### Post by nathanvy on 2014-10-07
> **T.J. said:**
> To answer your question directly, I do not know.Ok, I'll try it, then.  Thanks.

> It would help if you told me what wm you had in mind.

awesomewm

> **nathanvy said:**
> 
What I would like to do is:
[LIST]
[*]Remove my DE (gnome) entirely, including gdm
[*]**install awesome wm and SLiM**
[*]Still have gorgeous fonts
[/LIST]


---

### Post by grahammechanical on 2014-10-07
Ubuntu has its own fonts.

[http://font.ubuntu.com/](http://font.ubuntu.com/)

The package name is ttf-ubuntu-font-family. At least that is what Synaptic tells me I have installed on my Ubuntu.

Regards.

---

