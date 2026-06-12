---
title: "Customize xterm"
date: 2007-03-18
forum: General Help
---

### Post by axrh on 2007-03-18
Hi guys,

How should I go about customizing xterm?  I would like to change the font, font size, etc.  Also, is there a key stroke that increases the font?

Thanks!

---

### Post by llamakc on 2007-03-18
This is documented ALL over the web. You can either create individual aliases or launchers with the specifics you want, or set them in your ~/.Xdefaults file.

---

### Post by kerry_s on 2007-03-18
The menu can be viewed by holding ctrl + mouse, all three buttons show a different menu.

For font size it would be the .Xdefaults file or what i did was go straight to the settings in /etc/X11/app-defaults/XTerm
look for this section->

```

*VT100.utf8Fonts.font2:	-misc-fixed-medium-r-normal--8-80-75-75-c-50-iso10646-1
#*VT100.utf8Fonts.font:	-misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso10646-1
*VT100.utf8Fonts.font:	-misc-fixed-medium-r-normal--20-200-75-75-c-100-iso10646-1
*VT100.utf8Fonts.font3:	-misc-fixed-medium-r-normal--14-130-75-75-c-70-iso10646-1
*VT100.utf8Fonts.font4:	-misc-fixed-medium-r-normal--13-120-75-75-c-80-iso10646-1
*VT100.utf8Fonts.font5:	-misc-fixed-medium-r-normal--18-120-100-100-c-90-iso10646-1
*VT100.utf8Fonts.font6:	-misc-fixed-medium-r-normal--20-200-75-75-c-100-iso10646-1

```

I just commented out the original and use the settings from the largest font(font6)

---

### Post by axrh on 2007-03-18
Thank you!

---

