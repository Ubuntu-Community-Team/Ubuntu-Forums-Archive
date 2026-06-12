---
title: "[SOLVED] Ubuntuforums font rendering"
date: 2008-02-05
forum: General Help
---

### Post by gwi on 2008-02-05
The Ubuntuforums pages all show up in bold font in Firefox (2.0.0.11). Why is that?

In Internet Explorer (6.0 under Wine) they are not bold. (I don't like the way IE renders the font, but at least it is not bold.)
See the attachments ff.png and ie.png.

As a sample of another page I included ff2.png, which shows a fragment of a Google page in Firefox.

Font settings in Firefox: serif (16px), sans-serif (16px), monospace (12px), no minimum size. See attached fffont.png.

Font settings in Gnome: 96dpi, anti-alias with full hinting (LCD).

---

### Post by kerry_s on 2008-02-05
don't let the web site choose the font, they look for windows fonts, in this case helevicta(aka:ariel), but they look like crap cause there's no clear type.your best bet for firefox is to uncheck the " let web sites select font " or disable bitmap fonts altogether(sudo dpkg-reconfigure fontconfig-config)

oops, forgot the pics->

---

### Post by gwi on 2008-02-06
Unchecking "let web site select font" messes up other sites. I already have bitmap fonts disabled.

Just discovered the cause of the problem: I only had Tahoma Bold installed, not Tahoma regular. Tahoma is the first font in the CSS of the Ubuntuforums site.

```
font: 12px Tahoma, Sans, Arial, Helvetica, sans-serif;
```

I think it is a bit silly to have a Windows font as primary font, for a Linux distribution's forums site. :confused:

Thanks for your reply anyway. It made me look inside the CSS, and put me on track of the missing Tahoma font.

---

