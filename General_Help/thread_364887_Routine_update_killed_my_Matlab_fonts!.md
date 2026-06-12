---
title: "Routine update killed my Matlab fonts!"
date: 2007-02-18
forum: General Help
---

### Post by Lucretia on 2007-02-18
FYI I'm running Edgy with the Feisty kernel, 32-bit version...

It seems like one of the routine Ubuntu updates in the last few weeks removed support for something, and now I have problems in Matlab (R2006a and b both had the issue). All of my graphs and dialog boxes do not display text. My graphs lack titles and labels, and dialog boxes have no text at all, other than on the buttons. Everything else displays normally.

Does anyone have an idea of what the problem is here?

---

### Post by ehowell on 2007-02-18
I'm not sure but I can't even get a desktop on 2007a due to a font error on Edgy 32bit. Mathworks and I are talking, if I find out anything I will post it up.

---

### Post by gp123 on 2007-04-09
I had similar problems with matlab fonts in figures. I found that manually adding font paths to the x server fixed it. Using the command:

```
xset q
```

I found that only one font directory on the font path, despite having a number of them specified in xorg.conf.  So, I added more using the commands:

```
xset fp+ /usr/share/fonts/X11/100dpi/:unscaled
xset fp+ /usr/share/fonts/X11/75dpi/:unscaled
xset fp+ /usr/share/fonts/X11/Type1
xset fp+ /usr/share/fonts/X11/100dpi
xset fp+ /usr/share/fonts/X11/75dpi
xset fp rehash
```

Then ran matlab, and everything was working as usual. 

These are all the font directories that were in my xorg.conf directory but weren't showing up for some reason. Only the first one listed, /usr/share/fonts/X11/misc would show up.

---

### Post by Rumo on 2007-04-11
My fonts in matlab are really tiny. 48 pt is barely readable. Btw the xset commands didn't work for me.

I'm not sure if this behaviour was caused by an update (I'm using kubuntu feisty) or by me:

In kde-systemsettings gtk styles&fonts I changed the setting "use another font" to "use my kde fonts in gtk applications". Problem is it's impossible to change it back. Here's the bug report I filed: [https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/105454](https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/105454)

---

### Post by Lucretia on 2007-04-11
I just tried xset q, and all the fonts were listed. No luck :-(

Just to be clear on what's happening, here's a screenshot:

[IMG]http://farm1.static.flickr.com/239/455954835_76765dc9a6.jpg?v=0[/IMG]

(Sorry about the small size, but flickr doesn't seem to let me have it any bigger)

Not only are the fonts missing on my plots, but Matlab isn't drawing the graph so that it takes up the entire plot, if you see what I mean. I'm not using xlim or anything like that. This is what it's doing by default.

---

### Post by ecoxmit on 2007-05-02
i have the same problem with tiny fonts as rumo. any luck in fixing that?

---

