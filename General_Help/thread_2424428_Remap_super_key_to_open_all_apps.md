---
title: "Remap super key to open all apps"
date: 2019-08-08
forum: General Help
---

### Post by tyw7 on 2019-08-08
I can't remove the super key binding from show over view.  I changed it to super+tab but the system is still using the super key binding to show over view.

---

### Post by deadflowr on 2019-08-08
What do you mean by open all apps?
Do you mean show all apps running? Like what a show desktop feature does.
Or do you mean open all apps at once?; all 30 to 100+ apps you may have installed on the desktop.

And where did you change the settings at? Or with what...

---

### Post by tyw7 on 2019-08-10
Currently the windows key was mapped to "overall" option with no way to change it.

I tried changing the option in the "shortcuts" setting.


I want to map it to show the all apps menu (super+a), as with Chrome OS and the Window start menu.

---

### Post by deadflowr on 2019-08-10
It seems that particular key mapping is part of another system setting not included in the default settings.
It's changeable in Gnome tweaks, dconf-editor or the comman line gsettings utility.
I'd recommend install Gnome Tweaks (should show as Tweaks in Software store) as it has multiple uses.
(Tweaks can help easily set themes and allows control of any installed gnome extensions, and other settings as well)

But you can also run this one time command line to disable that particular keybinding
```
gsettings set org.gnome.mutter overlay-key ''
```
That will change it from Super_L to a blank effectively disabling it.
Then you should be able to remap it to something else.

---

