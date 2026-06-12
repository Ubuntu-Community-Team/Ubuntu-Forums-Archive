---
title: "Keeps returning to the login screen."
date: 2008-01-29
forum: General Help
---

### Post by ender193 on 2008-01-29
All,

I recently switched the screen resolution in system preferences, and upon hitting Apply, the system went to the login screen.  Trying to login with that username, the screen goes blank, it gets to the point where it tries to run the rc.local script, and then it goes back to the login screen again.  It does this over and over.  I have rebooted and get the same response.  It will not even let me login in failsafe Gnome.  The only thing I can get to on that login is the failsafe terminal.  Other users on the machine can still login as normal.

Here is my .xsession-errors file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup...
The application 'x-session-manager' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

I am running Feisty on a Dell Inspiron 6000.

Any suggestions on how to recover from this?

Thanks,

Ez

---

### Post by yabbadabbadont on 2008-01-29
Try renaming the hidden ".metacity" directory in your home directory.  Sessions are stored there.  In the terminal, you would run something like ```
mv .metacity .metacity.borked
```  Then logout and back in.  A new directory should be created with the default settings.  NOTE that the directory is hidden because the name starts with a period.  If that doesn't help, try doing the same for the ".gconf*" and ".gnome*" directories.

---

### Post by steveneddy on 2008-01-29
I think he needs to reconfigure the xserver.

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

what video card are you using?

---

### Post by ender193 on 2008-01-30
Thanks for the help.

I isolated the problem to the .gconf directory.  Replacing the entire thing allowed me to login, however my desktop settings were back to the defaults.  I restored the .gconf dir and then deleted the following directory:

~/.gconf/desktop/gnome/screen

I was then able to login and all my desktop settings were saved.

No more problem!  Thanks all!

---

