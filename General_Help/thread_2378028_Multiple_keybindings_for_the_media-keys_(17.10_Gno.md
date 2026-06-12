---
title: "Multiple keybindings for the media-keys (17.10 Gnome Wayland)"
date: 2017-11-19
forum: General Help
---

### Post by jarvo2 on 2017-11-19
How can I set up multiple keybindings for the media keys? **org.gnome.settings-daemon.plugins.media-keys**
 
are using **String** -type and not the **String Array** type that **org.gnome.desktop.wm.keybindings** use.

wiki.ubuntu.com gives an example only for adding multiple keybinds only for the desktop shortcuts;
> **Multiple Keybindings**

 ...you can make it work using dconf-editor.  For  example to have "Close window" use both the traditional <Alt>F4 as  well as an easier to hit Pause/Break button, change  **org.gnome.desktop.wm.keybindings** close to ['Pause', '<Alt>F4']. 


This does not apply for the media shortcuts.

Any help is appreciated. I'm somewhat a keyboard virtuoso.

-Joonas

Edit: Fixed the wrong location for the media-keys.

---

### Post by go1255 on 2017-11-20
Not an answer to your question, but in case you're looking for a replacement for 'xdotool XF86AudioPlay' etc under Wayland (which I was when I found your post), I used [https://github.com/acrisci/playerctl](https://github.com/acrisci/playerctl) and mapped 'playerctl play-pause' to a keyboard shortcut using the normal GNOME Settings.

---

