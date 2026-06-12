---
title: "Window buttons on wrong side in KDE"
date: 2017-04-02
forum: General Help
---

### Post by tomsk3 on 2017-04-02
Hello, Im using KDE desktop and I like some classic Gnome apps more than KDE's, for example I like more Image Viewer (Eye of Gnome) more than KDE's default.. or I like more Gnome terminal than Konsole in Kubuntu. But my problem is that these gnome apps have window buttons (close, maximize, minimize) on the right side, but I like to have these buttons on the left side (like in Unity), KDE's apps are ok, they have these buttons on the left side, but gnome apps dont. 

Is it possible to change position of Window buttons to left in gnome apps?

Thank you

---

### Post by dragonfly41 on 2017-04-02
This thread [http://askubuntu.com/questions/9867/how-to-switch-window-controls-to-the-left-gnome-shell](http://askubuntu.com/questions/9867/how-to-switch-window-controls-to-the-left-gnome-shell)
suggests using dconf-editor.

My setting in Ubuntu 14.04 is button-layout   :close
and it seems that you need to edit this to be    :[COLOR=#111111][FONT=Consolas]close,minimize,maximize:

but you will need to experiment since I have not changed these settings[/FONT][/COLOR]

---

### Post by tomsk3 on 2017-04-02
I dont have a **shell** in **org -> gnome :sad:**

---

### Post by dragonfly41 on 2017-04-02
I don't know why your shell is missing. But reading other threads I would try running

```
[COLOR=#111111][FONT=Consolas]gsettings set  org.gnome.shell.overrides button-layout ':minimize,maximize,close'
```[/FONT][/COLOR]

---

### Post by tomsk3 on 2017-04-03
No such schema 'org.gnome.shell.overrides'


:(

---

### Post by dragonfly41 on 2017-04-03
That command I found here ... [http://askubuntu.com/questions/125765/how-do-i-add-minimize-maximize-buttons-to-gnome-shell-windows](http://askubuntu.com/questions/125765/how-do-i-add-minimize-maximize-buttons-to-gnome-shell-windows) ...
may be for an earlier version of Ubuntu.

An alternative command (for 14.04) is given as ...

```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides "{'Gtk/DecorationLayout': <':minimize,maximize,close'>}"
```

But you should have enough clues now to look around to solve this for whatever version of Ubuntu you have installed (you have not clarified your version of Ubuntu).

It may be that this does not apply to KDE desktop.

---

### Post by tomsk3 on 2017-04-03
> **dragonfly41 said:**
> That command I found here ... [http://askubuntu.com/questions/125765/how-do-i-add-minimize-maximize-buttons-to-gnome-shell-windows](http://askubuntu.com/questions/125765/how-do-i-add-minimize-maximize-buttons-to-gnome-shell-windows) ...
may be for an earlier version of Ubuntu.

An alternative command (for 14.04) is given as ...

```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides "{'Gtk/DecorationLayout': <':minimize,maximize,close'>}"
```

But you should have enough clues now to look around to solve this for whatever version of Ubuntu you have installed (you have not clarified your version of Ubuntu).

It may be that this does not apply to KDE desktop.

yea this works but nothing changed :D

---

### Post by dragonfly41 on 2017-04-03
> [COLOR=#000000]yea this works but nothing changed [/COLOR][COLOR=#000000]
I'm not sure what this means.
Perhaps a log out / log in is required before changes take effect?
But that is a guess.[/COLOR]

---

