---
title: "gnome-terminal, how to change just one window"
date: 2018-12-08
forum: General Help
---

### Post by Skaperen on 2018-12-08
i have multiple gnome-terminal windows open and i would like to change the font size and geometry of _just *one* window_, leaving _*all* the others_ *unchanged*.

when i try to change one window, it changes all the others.  i suspect this is because of the profile name being shared by them all.

1.  is there some way to accomplish the changes (not to be saved) on just one window?

2.  is there a way to change the profile name of one terminal window (and not the others)?

---

### Post by again? on 2018-12-08
If you can't find a solution with gnome-terminal, take a look at xfce4-terminal where you can use a separate config
or use the --zoom option.
[https://forum.xfce.org/viewtopic.php?id=9188](https://forum.xfce.org/viewtopic.php?id=9188)

---

### Post by Skaperen on 2018-12-08
how well will it work under unity?  how easy is it to reconfigure by text editing (like with emacs, gedit, jed, nano, pico, sed, or vim) or must i run the terminal program to reconfigure it from the impossible-to-read colors it was mistakenly configured to use?

---

### Post by again? on 2018-12-08
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt depends xfce4-terminal**
xfce4-terminal
  Depends: exo-utils
  Depends: libc6 (>= 2.4)
  Depends: libcairo2 (>= 1.2.4)
  Depends: libgdk-pixbuf2.0-0 (>= 2.22.0)
  Depends: libglib2.0-0 (>= 2.37.3)
  Depends: libgtk-3-0 (>= 3.21.5)
  Depends: libpango-1.0-0 (>= 1.14.0)
  Depends: libvte-2.91-0 (>= 0.51.90)
  Depends: libx11-6
  Depends: libxfce4ui-2-0 (>= 4.11.0)
  Depends: libxfce4util7 (>= 4.9.0)
 |Recommends: <default-dbus-session-bus>
    dbus-user-session:i386
    dbus-user-session
  Recommends: <dbus-session-bus>
    dbus-user-session:i386
    dbus-user-session
    dbus-x11:i386
    dbus-x11
```

Config resides @ ~/.config/xfce4/terminal/terminalrc or override with individual options.
```
[B][COLOR="#006400"]glen@Bionic:~$[/COLOR] xfce4-terminal --help
Usage:[/B]
  xfce4-terminal [OPTION...]

General Options:
  -h, --help; -V, --version; --disable-server; --color-table; --preferences;
  --default-display=display; --default-working-directory=directory

Window or Tab Separators:
  --tab; --window

Tab Options:
  -x, --execute; -e, --command=command; -T, --title=title;
  --dynamic-title-mode=mode ('replace', 'before', 'after', 'none');
  --initial-title=title; --working-directory=directory; -H, --hold;
  --active-tab; --color-text=color; --color-bg=color

Window Options:
  --display=display; --geometry=geometry; --role=role; --drop-down;
  --startup-id=string; -I, --icon=icon; --fullscreen; --maximize; --minimize;
  --show-menubar, --hide-menubar; --show-borders, --hide-borders;
  --show-toolbar, --hide-toolbar; --show-scrollbar, --hide-scrollbar;
  --font=font; --zoom=zoom

See the xfce4-terminal man page for full explanation of the options above.
```

---

### Post by vanadium on 2018-12-09
gnome-terminal has --window-with-profile=PROFILENAME and  --tab-with-profile=PROFILENAME, so I suppose it is possible to load a separate window with a different appearance.

---

### Post by Skaperen on 2018-12-09
you've gotten me interested.  actually, tabs did that.  i have lots of questions, but at this point it makes sense to just try it.  i've been thinking that xfce is the de that i could switch to for 20.04 LTS.

---

### Post by Skaperen on 2018-12-13
> **guber2 said:**
> If you can't find a solution with gnome-terminal, take a look at xfce4-terminal where you can use a separate config
or use the --zoom option.
[https://forum.xfce.org/viewtopic.php?id=9188](https://forum.xfce.org/viewtopic.php?id=9188)

looks good.  it looks like it is a workable drop-in replacement (same fonts and geometry gets the same size).

is there a forum/community specific to xfce4-terminal as opposed to the general xfce/xubuntu forum.

---

