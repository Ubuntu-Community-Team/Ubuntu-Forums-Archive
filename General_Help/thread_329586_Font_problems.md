---
title: "Font problems"
date: 2007-01-01
forum: General Help
---

### Post by Icemanyurt on 2007-01-01
I am looking for a font pack with standard windows fonts (Times New Roman, Aerial, etc...) so I can ensure my documents are readable on both Unbuntu and WindowsXP.  

I am really not sure how to install font packs and the such, so any help and small words would be great :)

---

### Post by fragos on 2007-01-01
Use Synaptic to install package "msttcorefonts".  His has the most popular Microsoft fonts.

---

### Post by Icemanyurt on 2007-01-06
Thanks, that worked like a charm!

---

### Post by guice on 2007-01-14
> **fragos said:**
> Use Synaptic to install package "msttcorefonts".  His has the most popular Microsoft fonts.
I have that package installed, but MS documents still look horriable under OpenOffice. Is there something else I'm missing?

I've attached a copy of a word document opened in OpenOffice. You can see the fonts, including the menu fonts, look horrible.

---

### Post by madrano on 2007-01-14
[http://ubuntuexperiences.blogspot.com/2007/01/subpixel-rendering-packages-for-ubuntu.html](http://ubuntuexperiences.blogspot.com/2007/01/subpixel-rendering-packages-for-ubuntu.html)

---

### Post by guice on 2007-01-14
> **madrano said:**
> [http://ubuntuexperiences.blogspot.com/2007/01/subpixel-rendering-packages-for-ubuntu.html](http://ubuntuexperiences.blogspot.com/2007/01/subpixel-rendering-packages-for-ubuntu.html)

Did that. You can totally see the fonts being rendered properly. I even insured "always" was selected to and "No" on bitmap fonts.

Screen shot attached to show all of the OS rendered fine, but OpenOffice. I even restarted X.

---

### Post by fragos on 2007-01-14
For setting rendering, I stick to the simple Gnome GUI approach System-> Preferences-> Font.  It gives you four choices and shows the results side by side.  It is posible to adjust rendering in a more finer grained way but this makes it easier to see the end result.  The worst results on my color LCD are when monochrome is selected.  This looks somewhat like what you have.  It seems that font rendering in OpenOffice is different than the system in general and they've been workoing to improve it.  My results are much better than yours.  There is an OpenOffice 2.1 release that hasn't worked its way into the Ubuntu repositories yet.  I've seen Ubuntu DEB packages mentioned in the forum.  I'd certainly try the 2.1.

---

### Post by guice on 2007-01-14
Ah ha, installing OpenOffice 2.1 did it. Looks MUCH better now. Hell, now feels like a real application after that. Thanks!

---

