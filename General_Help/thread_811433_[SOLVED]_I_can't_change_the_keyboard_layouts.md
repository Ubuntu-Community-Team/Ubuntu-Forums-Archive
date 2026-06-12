---
title: "[SOLVED] I can't change the keyboard layouts"
date: 2008-05-29
forum: General Help
---

### Post by white_eagle-mk on 2008-05-29
I was unpleasantly surprised yesterday when I found out that I couldn't change the keyboard layout to MK (Macedonian) anymore with both the keyboard shortcut and the panel indicator, so I went to keyboard preferences clicked on the "Layouts" tab then I clicked on the button labeled reset to defaults and then this window (attached to this post) hoped up and the Macedonian layout was erased, but If I wanted to re add it then the same window showed up and although the language was added I couldn't change to it. As that window told me, I will post the result of ```
xprop -root | grep XKB
``` and of ```
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```. Here it is now after I reseted the settings once more (the macedonian layout isn't there) ```
whiteeagle@whiteeagle-laptop:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "en", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "en", ""
whiteeagle@whiteeagle-laptop:~$  gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = 
 overrideSettings = true
 options = []
whiteeagle@whiteeagle-laptop:~$ 
```
And here it is when the Macedonian layout is re added (but I can't change to it):
```
whiteeagle@whiteeagle-laptop:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "en", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "en", ""
whiteeagle@whiteeagle-laptop:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us	en,mk]
 model = 
 options = [grp	grp:alts_toggle]
 overrideSettings = true
whiteeagle@whiteeagle-laptop:~$ 

```

---

