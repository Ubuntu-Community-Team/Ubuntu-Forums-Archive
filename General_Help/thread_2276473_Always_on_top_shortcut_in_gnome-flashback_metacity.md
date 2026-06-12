---
title: "Always on top shortcut in gnome-flashback metacity"
date: 2015-05-02
forum: General Help
---

### Post by luvshines on 2015-05-02
Hey
I had this weird issue, and still having, I described here: [http://ubuntuforums.org/showthread.php?t=2269986](http://ubuntuforums.org/showthread.php?t=2269986)

As a workaround I am using gnome-flashback with metacity.
But I miss 'always on top' shortcut which I had set in Compiz

I couldn't seem to find 'toggle_above' window_keybinding in gconf-editor as was suggested in some posts.

I don't want to right click and choose every time. Just want to set 'alt + a' as a shortcut to toggle and make my life easy

Any suggestions would be much appreciated

---

### Post by luvshines on 2015-05-04
Well, the issue I posted in that other link is solved now.

But I would still appreciate if this is solved too.

BUMPING !!

---

### Post by CantankRus on 2015-05-05
Hi again luvshines,
Check what your current keybinding is via terminal....
```
gsettings get org.gnome.desktop.wm.keybindings toggle-above
```

Mine was set to **ctrl+shift+a**
To set to this shortcut, run...
```
gsettings set org.gnome.desktop.wm.keybindings toggle-above "['<Control><Shift>a']"
```

To set to **alt+a**, run...
```
gsettings set org.gnome.desktop.wm.keybindings toggle-above "['<Alt>a']"
```

******* I don't think this works in unity 
Instead you can create a custom shortcut to run a **wmctrl** command.
Install wmctrl ...
```
sudo apt-get install wmctrl
```

Then create a custom shortcut using as the command 
```
wmctrl -r :ACTIVE: -b toggle,above
```

---

### Post by luvshines on 2015-05-09
For gnome-flashback:
Found the toggle-above in dconf-editor. I was looking into gconf-editor earlier

For Unity:
Here I can set the shortcut by installing compiz plugin extra, then in ccsm 'extra wm action'

---

### Post by CantankRus on 2015-05-09
> **luvshines said:**
> For gnome-flashback:
Found the toggle-above in dconf-editor. I was looking into gconf-editor earlier

For Unity:
Here I can set the shortcut by installing compiz plugin extra, then in ccsm 'extra wm action'
Ahhh nice find. =d> Forgot about that plugin even though **compiz-plugins** is installed.

---

