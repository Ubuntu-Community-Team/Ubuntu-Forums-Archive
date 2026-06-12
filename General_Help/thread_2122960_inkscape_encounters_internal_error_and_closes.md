---
title: "inkscape encounters internal error and closes"
date: 2013-03-06
forum: General Help
---

### Post by snowlizard31 on 2013-03-06
I just installed inkscpae via the ubuntu softwhere center and everytime i open it it opens the application but immediately pops up a notification saying inkscape encountered an interal error and closes

---

### Post by r-senior on 2013-03-06
Which version of Ubuntu are you running?

A couple of things to try:

1. Open up a terminal and run it from there so that you can see any error messages:

```
inkscape
```

Post any that you see, unless they are just warnings about fonts and such.

2. Try reinstalling it.

```
sudo apt-get install --reinstall inkscape
```

---

### Post by snowlizard31 on 2013-03-06
I'm running xubuntu 12.04. I just figured it out thanks to you recomending to open inkscape on the terminal. It seems the problem was  with the icons theme i was using I switch icons themes and it works now but can you help me get it to run with the icon theme?

```

(inkscape:7274): Gtk-WARNING **: Theme directory actions of theme OSX_Aluminium has no size field


(inkscape:7274): Gtk-WARNING **: Theme directory 128x128 of theme OSX_Aluminium has no size field

**
Gtk:ERROR:/build/buildd/gtk+2.0-2.24.10/gtk/gtkrecentmanager.c:2073:get_icon_fallback: assertion failed: (retval != NULL)

Emergency save activated!
Emergency save completed. Inkscape will close now.
If you can reproduce this crash, please file a bug at www.inkscape.org
with a detailed description of the steps leading to the crash, so we can fix it.
Aborted (core dumped)


```

---

### Post by r-senior on 2013-03-06
Inkscape is a bit weird with icons in menus on 12.04. I used to get a lot of empty ones and I ended up installing the nightly build from this PPA:

[https://launchpad.net/~inkscape.dev/+archive/trunk](https://launchpad.net/~inkscape.dev/+archive/trunk)

I use Inkscape quite a bit for making icons and this nightly has not crashed on me or caused me problems. Obviously YMMV.

The other thing I had to do was disable the global menu. Simply copy /usr/local/share/applications/inkscape.desktop to ~/.local/share/applications/ and edit the exec line so that it looks like this:

```
Exec=env UBUNTU_MENUPROXY=0 inkscape %F
```

Actually, I'd try this first, then the PPA version. I don't really remember which fixed my icons.

---

### Post by snowlizard31 on 2013-03-07
cool thanks I'll try it out and see if it works!

---

