---
title: "Looking for the command to add to Xscreensaver"
date: 2014-01-13
forum: General Help
---

### Post by jacatone on 2014-01-13
I'm using Ubuntu 12.04. I removed the gnome-screensaver and added xscreensaver. I need to add it to my startup programs. Anyone the command I add to the Startup window so the screensaver launches when I login? Thanks.

---

### Post by Dennis N on 2014-01-13
htop shows it to be [B]xscreensaver -no-splash
[/B]

---

### Post by steeldriver on 2014-01-13
I think you just need to run the xscreensaver-demo program - from the xscreensaver man page:

```

CONFIGURATION
       The easiest way to configure xscreensaver is to simply run the xscreen&#8208;
       saver-demo(1) program, and change the settings through  the  GUI.   The
       rest  of  this  manual page describes lower level ways of changing set&#8208;
       tings.

       I'll repeat that because it's important:

           The easy way to configure xscreensaver is to run the  xscreensaver-
           demo(1)  program.   You  shouldn't  need  to  know any of the stuff
           described in this manual unless you  are  trying  to  do  something
           tricky, like customize xscreensaver for site-wide use or something.

       Options to xscreensaver are stored in one of two places: in a .xscreen&#8208;
       saver file in your home directory; or in the X resource  database.   If
       the  .xscreensaver  file  exists,  it  overrides  any  settings  in the
       resource database.

```

---

### Post by Dennis N on 2014-01-14
_Information for users wanting to use xscreensaver in Ubuntu 12.04 (which comes with gnome-screensaver)_

Replacing **gnome-screensaver** by **xscreensaver** in Ubuntu (tested in 12.04) can be done without uninstalling gnome-screensaver. Just uncheck gnome-screensaver in the startup applications list (it's listed there as screensaver), then install and add xscreensaver to this list and mark its checkbox. Command to use: **[FONT=Courier New]xscreensaver -no-splash[/FONT]**

To expose all startup applications, follow the advice here (needed to see the screensaver entry):
[http://ubuntuguide.net/how-to-show-all-startup-applications-in-ubuntu-12-04-lts](http://ubuntuguide.net/how-to-show-all-startup-applications-in-ubuntu-12-04-lts)

Search for screensaver in Dash to set your preferences.

xscreensaver has only a few screensavers. You should also install:
[B]xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra[/B]
to have a full selection.

---

