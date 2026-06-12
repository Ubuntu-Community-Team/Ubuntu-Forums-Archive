---
title: "Save Gnome panel layout?"
date: 2007-01-20
forum: General Help
---

### Post by Mr. Picklesworth on 2007-01-20
I am very particular about how my panels are arranged, but this beautiful layout often gets muddled up.

Where is my Gnome desktop's panel layout stored?
Or, even better, is there a program which I can use to save / restore the layout?

---

### Post by mcduck on 2007-01-20
I don't think that there's easy way to save it, but it's possible to lock panel layout and that should prevent it from changing:

1. Press Alt-F2 and run 'gconf-editor'
2. Browse to apps/panel/global
3. enable 'locked_down'

If you want to change anything in your panels after that you need to disable the 'locked_down' key before you can do anything.

---

### Post by 23meg on 2007-01-20
[https://wiki.ubuntu.com/PanelSwitcher](https://wiki.ubuntu.com/PanelSwitcher)

---

### Post by Mr. Picklesworth on 2007-01-21
Thanks 23Meg and MCDuck!

After finally creating a launcher for it (I had to make a shell script, then get the launcher to run that, because it seems that Launchers cannot call cd and have no "Run this program from" value)... (urk, what a mess!) after creating a launcher for it, I ran it and it worked well.
I was even inspired to come up with a newer, cooler layout with some fancy changes in gconf-editor :)

Speaking of gconf-editor... Is there a way to get rid of old panel configuratios that are no longer in use?
It's a bit crazy that the Gnome configuration has over 10 different panels listed when only one is actually in use.
(And will removing those configurations stop that layout from working via PanelSwitcher?).

Also a really off topic question. (Yay, derailing my own thread!)
Your link led me to discover a fancy SessionBackup thing. It sounds like it isn't really being developed anymore, though, so do you know of an alternative?

(Oh, and above all: Thanks Peter Moberg!)

---

### Post by OzzyFrank on 2007-09-02
Can you show us that script, as I am wanting to start making scripts for little things like that, so it would be a help in learning. Cheers

---

### Post by jamesrl on 2008-03-08
To save your panel settings from the command line (which are saved in the gconf, which you can access by the GUI gconf-editor or from the command line with gconftool-2 ), type in

```

gconftool-2 --dump /apps/panel > ~/settings/saved_panel_settings.entries

```
I saved them into a file in the settings directory called saved_panel_settings.entries ... you can name it anything you want.
To then load these new settings run:
```

## loads settings into gconf
  gconftool-2 --load ~/settings/saved_panel_settings.entries
## kills the gnome-panel so it restarts with the new gconf settings
  killall gnome-panel
## restart gnome network monitor applet which dies after killall gnome-panel
  nm-applet &

```

I find this more handy the the GUI panelswitcher app, as I can then put this into scripts (e.g. switching into single/multiple monitor layout, can load panel settings for single/multiple monitors).

---

### Post by psypher on 2008-03-10
aweome thanks you that did the trick. damn it's been annoying me.

---

