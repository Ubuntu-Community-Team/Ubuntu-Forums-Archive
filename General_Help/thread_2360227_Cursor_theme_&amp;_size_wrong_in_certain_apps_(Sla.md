---
title: "Cursor theme &amp; size wrong in certain apps (Slack, VS Code)"
date: 2017-05-02
forum: General Help
---

### Post by johnlbergqvist on 2017-05-02
I'm using Ubuntu 16.04 with the cinnamon desktop, and the cursor theme & size (redglass, 24) is being ignored within certain apps, such as Slack and Visual Studio Code) - instead they show the DMZ-White theme.

I've explicitly set the cursor to redglass via the following methods:
_dconf-editor (both my own user and the lightdm user)_
[LIST]
[*]org.cinnamon.desktop.interface.cursor_theme
[*]org.gnome.desktop.interface.cursor_theme
[*]org.mate.peripherals.mouse.cursor_theme
[/LIST]
[U]
gconf-editor[/U]_ (both my own user and the lightdm user)_
[LIST]
[*]desktop/gnome/peripherals/mouse/cursor_theme
[/LIST]

_update-alternatives_

[LIST]
[*]--config x-cursor-theme has been manually set to redglass
[/LIST]
_/var/lib/lightdm/.icons/default/index.theme, _[U]~/.icons/default/index.theme and /user/share/icons/default/index.theme
[/U]```
[Icon Theme]
Inherits=redglass

```

/etc/X11/Xresources/x11-common, /var/lib/lightdm/.Xdefaults and ~/.Xdefaults contain ```
Xcursor.theme: redglass
```

I can't see what else i've missed for VsCode & slack to be ignoring these settings. Is it because they're possibly web apps in some way?

---

### Post by johnlbergqvist on 2017-05-02
OK, it turns out I had a stray .Xresources in my home directory that was overriding the system defaults for vs-code & slack. (Except the rest of the system was ignoring that file it seems)

---

### Post by cmcanulty on 2017-05-03
This has been an annoying bug in all buntus for years. I really think it should be a priority bug fix. Some computers will not keep the mouse settings no matter how many tweaks. This is one of the few things windows has beat linux on.

---

