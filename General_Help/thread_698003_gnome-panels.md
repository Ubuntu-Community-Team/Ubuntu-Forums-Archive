---
title: "gnome-panels"
date: 2008-02-15
forum: General Help
---

### Post by nzadLithium on 2008-02-15
Hey

When i run games through wine my gnome-panels get repositioned. I have dual screens and i stick the panels on the one on the right. After running any fullscreen wine apps both panels are shoved at the top of the left screen. Is there a way i can reposition using a bash script?
(so i can add to end of my bash script for launching my game :) )

---

### Post by me208 on 2008-02-18
I would suggest just restart the panels with

```
killall gnome-panel
```

(possibly kill-all i'm not sure)

---

### Post by nzadLithium on 2008-02-18
i'll try that. thx for the idea

---

### Post by jamesrl on 2008-03-08
gnome-panels info are stored in the gconf settings (e.g., you can see in the gui in the gconf-editor) located in /apps/panel
If killall gnome-panel didn't work, here's what you do.

Get the settings how you like them, and then use gconftool-2 to dump the settings into a XML (formatted text file) somewhere.
like so
```

gconftool-2 --dump /apps/panel > ~/multiple_monitor_panels.entries

```

Then after you run your game, you can reload the settings by
```

## this loads the new XML values into gconf
gconftool-2 --load ~/multiple_monitor_panels.entries

# this reloads the panel settings to the new gconf values
killall gnome-panel

# this restarts gnome network monitor which you lose after the killall gnome-panels
nm-applet &

```

This same procedure can be used to have multiple panel configurations (or just have a backup of the panel configured how you like it, in case it gets screwed up accidentally).  There's also a panel switcher app with a GUI written in python

[https://wiki.ubuntu.com/PanelSwitcher]("https://wiki.ubuntu.com/PanelSwitcher"), but you can't call from the command line.  [Have to checkout from svn and then run
```

## checkout from subversion -- might have to 'sudo apt-get install subversion' first
svn checkout http://panelswitcher.googlecode.com/svn/trunk/ panelswitcher-read-only
## go into panelswitcher
cd panelswitcher-read-only/source/
python panelswitcher.py

```

---

