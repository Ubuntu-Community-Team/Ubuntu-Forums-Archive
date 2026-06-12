---
title: "Thunar Toolbar Icons TOO BIG (in 12.04)"
date: 2012-11-01
forum: General Help
---

### Post by woodyg on 2012-11-01
Hi,
more than 4 years ago someone mentioned ([here]("http://ubuntuforums.org/showthread.php?t=906638")) that in Thunar "the icons on the toolbar look like they are 48x48 pixels, and it should be smaller than that". I noticed the same problem in 11.10 and now also in 12.04 (Thunar is 1.2.3). Unfortunately the viewpoint from the developers is that it isn't a Thunar problem ([bugzilla]("https://bugzilla.xfce.org/show_bug.cgi?id=3971")), so there is no progress on this issue.
Does anyone know a fix that works ([this does not work]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/203236/comments/19"))?

---

### Post by Frogs Hair on 2012-11-01
I can reproduce the large icons only if I open Thunar in the Ubuntu session and only in the tool bar view. The path bar view is unaffected. The problem doesn't occur in the XFCE session though. I see no entry for Thunar in the dconf editor and I wonder if the theme fix is applicable Gnome 3 + .12.04 runs on top of Gnome 3.4 and uses GTK 3.4 themes.

---

### Post by woodyg on 2012-11-01
> **Frogs Hair said:**
> I can reproduce the large icons... only in the tool bar view. The path bar view is unaffected. 

I forgot to mention that. Yes, I prefer the tool bar view, as I want the back/forward button and the up button. In any case, there must be a problem somewhere. It is claimed it isn't a problem with Thunar, so where is the problem and what to do about it? :confused:

---

### Post by Frogs Hair on 2012-11-01
Home > hidden > .config > Thunar seems to have two configuration files the may hold the answer but I would have no idea what to change. It would require checking them line by line.

---

### Post by woodyg on 2012-11-02
:) Sorted! I found a patch that seems to have worked (**[this one]("https://launchpadlibrarian.net/12895227/thunar_toolbar_big_icons.patch")**). For those that are as unfamiliar with applying patches as I am, here is what I did:

```
sudo apt-get build-dep thunar
apt-get source thunar
cd thunar-1.2.3
wget -O - https://launchpadlibrarian.net/12895227/thunar_toolbar_big_icons.patch | patch -p1
./configure
make
sudo make install
```

---

### Post by Frogs Hair on 2012-11-02
Good to see you found a solution. I only use Thunar in XFCE so I was never aware of the issue until I saw your thread. :)

---

