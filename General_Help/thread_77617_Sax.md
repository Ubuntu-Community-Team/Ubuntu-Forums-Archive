---
title: "Sax ??"
date: 2005-10-17
forum: General Help
---

### Post by Storm Rider on 2005-10-17
Where can I find Sax or some other app to change the position of the display on my desktop?

---

### Post by dlpfmVfH on 2005-10-18
Can you give me some more information?
what do you mean by change the position of the display?

resolution??
colors??
how many virtual desktops??

---

### Post by Storm Rider on 2005-10-23
What I mean is that the desktop displeay iss to the right of the monitor, not centered.  
I could use the monitor buttons themselves but then the desktops on the other OS's I have installed would be off to the left.  

In Suse there is a gui called Sax that will let you change the number of colors, resolution and position of the display.:)

---

### Post by gherikill on 2005-10-24
I would also like to know if there is a equivalent to SAX2 in Kubuntu?  How do you change monitors/res and set up dual monitor support on Kubuntu?

---

### Post by shakin on 2005-10-24
Image position adjustments are, I think, handled by the driver. If you have an NVidia card you can use something such as [YanC](http://yanc.sourceforge.net/doc/doc-en.html) to do it. Xorg should also be able to do it using the xrandr. You'll need to add that extension to xorg.conf, then in the KDE Control Center under Preferences you can edit your Display properties. The Size & Orientation tab will be inactive unless you have xrandr enabled.

As for resolution changes, I know Gnome has a utility, but I forgot what the name was.

Dual monitors must be configured either through the driver manufacturer's tool (eg. dual head ATI card) or by configuring xorg.conf by hand.

---

### Post by Jengu on 2005-10-24
In Kubuntu, there are two ways to do it. First, there is the way that works in any distro that uses KDE. Right click on the desktop and click Configure Desktop. Then click on Display, and you'll see the options you need.

Or, if you're in Kubuntu, click the K-Menu -> System Settings -> Display which will bring you to the same place.

---

### Post by CompShrink on 2006-02-22
I'm considering on making it easier to use it in ubuntu, but for now if you don't mind compiling, which you probably do:

[http://sax.berlios.de/](http://sax.berlios.de/)
[ftp://ftp.berlios.de/pub/sax/README](ftp://ftp.berlios.de/pub/sax/README)

You can compile it, no debs that I know of that work in Ubuntu, or debs at all for that matter.

EDIT: I should really look at the age of the last post sometimes, sorry.

---

