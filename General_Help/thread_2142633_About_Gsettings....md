---
title: "About Gsettings..."
date: 2013-05-06
forum: General Help
---

### Post by fantab on 2013-05-06
I like the 'shade' feature which will roll the window up with middle-button click on title-bar, which was there upto 12.04. I see that it is replaced with 'toggle-shade' which is similar to 'shade' but it does not actually roll up the window. 

I tried to change it with gsettings:

```
$ gsettings set org.gnome.desktop.wm.preferences action-middle-click-titlebar shade
```

to which I get: "*The provided value is outside of the valid range*"

But in dconf-editor its description says:
[QUOTE=Description: action-middle-click-titlebar]This option determines the effects of middle-clicking on the title bar. **Current valid options are** 'toggle-shade', which will shade/unshade the window, 'toggle-maximize' which will maximize/unmaximize the window, 'toggle-maximize-horizontally' and 'toggle-maximize-vertically' which will maximize/unmaximize the window in that direction only, 'minimize' which will minimize the window, **'shade' which will roll the window up**, 'menu' which will display the window menu, 'lower' which will put the window behind all the others, and 'none' which will not do anything.[/QUOTE]

Also the drop-down value 'range' that dconf-editor gives for the schema are, "toggle-shade", "toggle-maximize", "toggle-maximize-horizontally" and "toggle-maximize-vertically".

However, the default value is set to 'lower', which by the way is also not listed in the dropdown values. But it can be set to 'lower'.

**How can I add value 'shade' to the schema?**
Need help in figuring this out...

---

### Post by mc4man on 2013-05-06
It appears the 'roll up/down' effect is gone, so it's won't matter even if you could add 'shade' to the schema (which you can't as it's not an enumerated value.

current allowed are
> $ gsettings range org.gnome.desktop.wm.preferences action-middle-click-titlebar
enum
'toggle-shade'
'toggle-maximize'
'toggle-maximize-horizontally'
'toggle-maximize-vertically'
'minimize'
'none'
'lower'
'menu'

even the scroll action on title-bar (gwd setting) is now only shade, unshade, no roll up/down effect

---

### Post by fantab on 2013-05-06
Thanks mc4man. Its sad to know that it is gone. I wish we can get it back, I simple loved the effect. Until then, its "toggle-shade".

---

