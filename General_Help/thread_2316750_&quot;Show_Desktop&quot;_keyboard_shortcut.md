---
title: "&quot;Show Desktop&quot; keyboard shortcut"
date: 2016-03-10
forum: General Help
---

### Post by lakeshore2985 on 2016-03-10
I'm trying to create a custom keyboard shortcut to "Show Desktop" icon.  Where is it or what is the command for it? Ubuntu 14.04.4 LTS.

---

### Post by maglin2 on 2016-03-10
Have a look under All Settings-Keyboard-Shortcuts-Navigation. There is a standard shortcut for hide/unhide all windows. Customize it if you wish by the instruction given at the bottom of the window.

Unless what you really want is to create a custom keyboard shortcut to the icon, not the icon's action, which is what your post implies?

---

### Post by mc4man on 2016-03-10
The default binding is ctrl+super+d
If you want to change do so in compizconfig-settings-manager (ccsm), ubuntu unity plugin, screens
(don't use a binding already in use outside of compiz or reserved for unity

---

### Post by lakeshore2985 on 2016-03-10
> **maglin2 said:**
> Have a look under All Settings-Keyboard-Shortcuts-Navigation. There is a standard shortcut for hide/unhide all windows. Customize it if you wish by the instruction given at the bottom of the window.  Unless what you really want is to create a custom keyboard shortcut to the icon, not the icon's action, which is what your post implies?  Yes, this is exactly what I want!   Thank you! And sorry if my original post confused you guys a little bit... I was asking about the "Show Desktop" icon because I wanted to find a way to not only use the icon in the launcher, but in other apps such as docks etc ("Plank" for example). But the keyboard shortcut "Super+D" does it for me!

---

### Post by Bucky Ball on 2016-03-10
Control+alt+d. That's it. You're on a clean desktop.

---

### Post by lakeshore2985 on 2016-03-11
> **Bucky Ball said:**
> Control+alt+d. That's it. You're on a clean desktop.  Nah... "Super+D", like the old days. Much beta! :)

---

### Post by Bucky Ball on 2016-03-12
> **lakeshore2985 said:**
> Nah... "Super+D", like the old days. Much beta! :)

No idea about the old days, but that keyboard combination doesn't work on my machine. Ctl+Alt+d = show desktop. Is super+d a windows thing? Dunno. :-k

---

### Post by vasa1 on 2016-03-12
> **Bucky Ball said:**
> No idea about the old days, but that keyboard combination doesn't work on my machine. Ctl+Alt+d = show desktop. Is super+d a windows thing? Dunno. :-k
```
    <keybind key="W-d">
      <action name="ToggleShowDesktop"/>
    </keybind>

```It's an [Openbox thing]("http://openbox.org/wiki/?title=Help:Actions&oldid=3651#ToggleShowDesktop") as well.

---

### Post by lakeshore2985 on 2016-03-12
Problem solved! Hooray! :D --> "**Settings-Keyboard-Shortcuts-Navigation**"

"Ctrl+Alt+D" just doesn't feel as good and fast as a simple two-keyed keyboard shortcut like "Super+D". Not sure who first started this, but I got it from Windows yes. In fact I did a little research and found previous versions of Ubuntu had it by default, but then changed to ugly weird "Ctrl+Alt+D", which doesn't make much sense. Many other Linux distros have many of the same most basic keyboard shortcuts as Windows such as "Super+E" (File Manager) and "Super+D" (Show Desktop), which lacks Ubuntu. Heck, Unity even lacks a proper taskbar which makes it very difficult to get used to and like.

Don't get me wrong I love Linux and Ubuntu (Debian), and I refuse to go back to Windows. But just because Windows is bad (and I agree completely) doesn't mean everything is bad... some of the good functions and ideas could be applied to Linux in order to make it more appealing to users switching to Linux, and keyboard shortcuts play an important part in improving speed and productivity.

 Just my opinion!

---

