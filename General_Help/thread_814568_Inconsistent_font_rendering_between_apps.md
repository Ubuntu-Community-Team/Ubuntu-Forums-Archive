---
title: "Inconsistent font rendering between apps"
date: 2008-05-31
forum: General Help
---

### Post by gladstone on 2008-05-31
I have hinting set to full with sub-pixel rendering on (RGB) for nice looking anti-aliased fonts in Hardy - much better than they have ever been IMO.

However there seems to be inconsistencies between programs (though I'm not talking about OpenOffice here :p). I use Opera & Smplayer frequently, which both use QT3(4).

I kind have solved it by doing the following:

[http://ubuntuforums.org/showpost.php?p=4683737&postcount=7](http://ubuntuforums.org/showpost.php?p=4683737&postcount=7)

but this isn't fully conclusive, for example:

Opera (QT3):
[[img]http://xs128.xs.to/xs128/08220/fonts1440.png.xs.jpg[/img]](http://xs128.xs.to/xs128/08220/fonts1440.png)

Firefox:
[[img]http://xs128.xs.to/xs128/08220/fonts1_ff645.png.xs.jpg[/img]](http://xs128.xs.to/xs128/08220/fonts1_ff645.png)

Opera:
[[img]http://xs128.xs.to/xs128/08220/fonts2739.png.xs.jpg[/img]](http://xs128.xs.to/xs128/08220/fonts2739.png)

Firefox:
[[img]http://xs128.xs.to/xs128/08220/fonts2_ff338.png.xs.jpg[/img]](http://xs128.xs.to/xs128/08220/fonts2_ff338.png)

Any ideas?

---

### Post by bingojed on 2008-11-16
Sorry for the late reply but I've been struggling with this too.

The final step is to edit ~/.opera/opera6.ini

In the [User Prefs] section, add or replace:
Enable Core X Fonts=0

There's also a setting for enabling/disabling Core X fonts in Opera:Config, but nothing made a difference for me until I made that change in opera6.ini.

Now Opera and Firefox both have smooth fonts (after turning on autohint in .fonts.conf and using slight hinting - full is too fuzzy).

---

### Post by kerry_s on 2008-11-16
sudo dpkg-reconfigure fontconfig-config

turn off bitmap fonts, log out and restart X (ctrl+alt+backspace)

---

