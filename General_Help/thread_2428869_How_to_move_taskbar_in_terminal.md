---
title: "How to move taskbar in terminal?"
date: 2019-10-10
forum: General Help
---

### Post by askul on 2019-10-10
Hi!

I have a laptop which screen has cracked from the left side, right where the taskbar is. Can one move it to top, down or right with some kinda terminal code?? I can open settings panel by clicking randomly, but in screen settings there´s no option to move taskbar.

Cheers!

-OA

---

### Post by CatKiller on 2019-10-10
I don't use Gnome, but ```
gsettings set org.gnome.shell.extensions.dash-to-dock dock-position RIGHT
``` might do it.

---

### Post by askul on 2019-10-10
"No such schema ´org.gnome.shell.extensions.dash-to-dock´"

Argh, i haven´t used Ubuntu for a long time and i should start from the scratch to get things familiar again.. So maybe i get a new laptop instead :D

---

### Post by ajgreeny on 2019-10-10
An alternative might be to use a different DE version such as Xubuntu, Ubuntu-Mate, Kubuntu, etc etc, all of which allow you to put the panel (taskbar) wherever you prefer.

---

### Post by PaulW2U on 2019-10-10
> **askul said:**
> "No such schema ´org.gnome.shell.extensions.dash-to-dock´"
That's probably because you have Ubuntu Dock installed instead of the functionally similar Dash to Dock.

If you install Dash to Dock from either the Ubuntu repositories or from the [extensions website]("https://extensions.gnome.org/extension/307/dash-to-dock/") then you'll find that appropriate settings are exposed in GNOME Tweak tool that allows you to reposition the dock away from the left hand side of your screen. You'll probably also have to disable Ubuntu Dock and might have to install GNOME Tweaks if you haven't already done so.

---

### Post by CatKiller on 2019-10-10
> **askul said:**
> "No such schema ´org.gnome.shell.extensions.dash-to-dock´"
Doing
```
gsettings --schemadir ~/.local/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com/schemas/ list-recursively org.gnome.shell.extensions.dash-to-dock
```
first apparently may help.

As I said, I don't use Gnome, so I can't test.

---

### Post by deadflowr on 2019-10-10
It's the right command for ubuntu dock, but that really points to needing to know more about which release of Ubuntu and what desktop is installed.
Might be unity...

---

