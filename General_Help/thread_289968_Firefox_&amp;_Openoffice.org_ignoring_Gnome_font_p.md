---
title: "Firefox &amp; Openoffice.org ignoring Gnome font prefrences"
date: 2006-10-31
forum: General Help
---

### Post by Frem on 2006-10-31
OpenOffice.org and Firefox 2.0 are ignoring my Gnome font settings after the edgy eft upgrade. They both appear to be rendering the fonts with some sort of subpixel smoothing type thing, and it looks blurry. They are doing this in the actual interface, not just documents and websites.

A picture is worth a thousand words, so I'm attaching an image that sums up the problem. 

Is there any way to fix this? I've deleted my gtkrc files to no avail.

---

### Post by happy-and-lost on 2006-10-31
Once you change font rendering prefs, you have to restart FF or OOo for the settings to take effect.

---

### Post by speedsix on 2006-10-31
Yeah I noticed this, firefox won't update until you restart it.

I find the subpixel(LCD) option the best, much sharper but some diagonals, particularly X's, look faint in parts.

---

### Post by Frem on 2006-11-01
Doh! That works, thanks.

---

### Post by dngpng on 2006-11-07
what if even I've restarted my OO or firefox? The difference is still there ... 

[IMG]http://dengpeng.name/upload/images/firefox-font-problem.png[/IMG]

and the out put of "xrdb -q | grep Xft" on my system is:
```

Xft.antialias:  1
Xft.dpi:        96.000000
Xft.hinting:    1
Xft.hintstyle:  hintfull
Xft.rgba:       rgb

```

---

### Post by dngpng on 2006-11-07
I found the reason: there is a useless .fonts.conf file in my home directory which I don't know when was generated. After deleting it, everything went normal. 

but there is another .fonts.conf which can magically make font rendering better: [http://www.ubuntuforums.org/showthread.php?t=275912](http://www.ubuntuforums.org/showthread.php?t=275912)

---

