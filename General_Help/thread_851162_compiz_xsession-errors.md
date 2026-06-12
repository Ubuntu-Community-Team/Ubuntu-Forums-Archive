---
title: "compiz xsession-errors"
date: 2008-07-06
forum: General Help
---

### Post by pasQualle on 2008-07-06
hey everybody,

after activating the extra visual effects and customizing them, I exported this preferences in the advanced desktop effects settings in a new profile. Suddenly I cannot boot my machine with the Xclient script. I think the problem is that I've overwritten ~/.profile with this export.

After the Login there appears an error message, that my session only lasted less than 10 seconds, and the following ~/.xsession-errors is displayed:

```
/etc/gdm/Xsession: Beginning session setup...
~/.profile: 1: [showdesktop]: not found
~/.profile: 2: s0_direction: not found
~/.profile: 4: [core]: not found
~/.profile: 5: as_active_plugins: not found
~/.profile: 5: svg: not found
~/.profile: 5: core: not found
~/.profile: 5: session: not found
~/.profile: 5: imgjpeg: not found
~/.profile: 5: workarounds: not found
~/.profile: 5: extrawm: not found
resize:  can't open terminal /dev/tty
~/.profile: 5: resizeinfo: not found
~/.profile: 5: regex: not found
~/.profile: 5: text: not found
~/.profile: 5: video: not found
~/.profile: 5: decoration: not found
~/.profile: 5: png: not found
~/.profile: 5: place: not found
~/.profile: 5: animation: not found
~/.profile: 5: dbus: not found
~/.profile: 5: move: not found
~/.profile: 5: loginout: not found
~/.profile: 5: snap: not found
~/.profile: 5: ring: not found
~/.profile: 5: expo: not found
~/.profile: 5: fade: not found
~/.profile: 5: scale: not found
~/.profile: 5: scaleaddon: not found
~/.profile: 5: scalefilter: not found
~/.profile: 6: s0_hsize: not found
~/.profile: 8: [resizeinfo]: not found
~/.profile: 9: as_always_show: not found
~/.profile: 11: [ring]: not found
~/.profile: 12: cannot open Alt: No such file
~/.profile: 12: as_next_key: not found
~/.profile: 13: Syntax error: redirection unexpected
```

So now. How can I restore the ~/.profile file, if this is the solution of the problem. And, for the next time, how can I save my personal compiz settings?

I really need your help here. And sorry for my quite bad english.

Pascal

---

### Post by ajgreeny on 2008-07-06
I did not think that this would stop you logging in, but perhaps because the ~/.profile file has been overwritten instead of just deleted, when I think it would be auto restored, this may be different.
Just in case it helps, here is a copy of the contents of my .profile file.  I have certainly not edited it in any way, and it seems to contain nothing very overwhelming, but finding a compiz profile in it instead of various user configurations my completely baffle the system.  See what happens if you rename the file .profile.bak and try a restart.  If that does not help, make a new .profile file with these contents in it

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```
If neither of these help, then I suspect it is not your .profile file that is causing the problem, but something else.
To save your compiz settings you should open CCSM System>>Preferences>>Advanced Desktop Effects Settings.  Go to Preferences, Profile and click on the Export button, as you appear to have done, but then name the profile as **compiz.profile**, or at least give it a name not just allow it to be .profile as this will do the same again.  In fact if you dont give it a .**profile** suffix at the end it will just be called **compiz** and will be in your home folder.  Of course it may simply be that you have enabled something in compiz that your machine can not manage.  This would not usually stop you logging in, however, so I think that is a bit less likely.
Good luck.  I hope you get it sorted

---

### Post by pasQualle on 2008-07-07
I tried the first variant and renamed the .profile to .profile.bak.

After the Login it took a while to generate/compile the desktop, but all of a sudden it worked. No new .profile file was generated.

Furthermore it is quite strange that when I have a look at the visual efects menu, no point it selected. And even after I activated the extra visual effects, there's still no .profile. The same for a reboot.

The other strange thing is, that, if I create a new profile in the preferences it's not possible to delete this profile, and in addition, if I customize my settings and export them in a file without the suffix .profile, the file remains empty.

But excluding all these small issues, it's working.

---

