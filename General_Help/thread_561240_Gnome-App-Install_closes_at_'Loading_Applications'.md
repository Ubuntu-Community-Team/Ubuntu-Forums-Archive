---
title: "Gnome-App-Install closes at 'Loading Applications'"
date: 2007-09-27
forum: General Help
---

### Post by NEUR0M4NCER on 2007-09-27
I've looked though all of the posts I can find, but the solutions to this problem seem to be many and varied. Add/Remove Programs just closes itself halfway through loading up. I'm running Feisty on a p4 1.5, nVidia (Envy), Compiz-Fusion. Everything's running just fine except for this. Trying to run it from a Terminal yields:

```
** (gnome-app-install:7748): WARNING **: return value of custom widget handler was not a GtkWidget
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 315, in <module>
    sys.argv, as, transient_for, addon_cd)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 262, in __init__
    self.updateCache(filter_to_restore)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 987, in updateCache
    activation_style=self.activation_style)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 123, in __init__
    self.refresh(progress)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 311, in refresh
    self.initListStores(item, self)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 379, in initListStores
    category.applications = gtk.TreeModelSort(category.filtered_applications)
SystemError: ../Python/getargs.c:1270: bad argument to internal function
```

... so I tried re-installing through Synaptic:

> app-install-data (version 0.3.31) will be re-installed
app-install-data-commercial (version 7.3) will be re-installed
gnome-app-install (version 0.3.31) will be re-installed

which works through okay, except for this:

```
Setting up app-install-data-commercial 7.3) ...
Can't import AppInstall.CoreMenu, aborting
```

I'm assuming that's where the problem lies, unless it's something to do with Python (?), but can't find any further info. Any help would really be appreciated.

---

### Post by rniella on 2007-09-27
It happened to me too, with different error messages but same result.  I`ve been looking for weeks for a solution but got nothing... I just dont know how to reinstall something like "gnome-app-install" without using Synaptic since it keeps giving me the same error, something r3garding Pyton..  I`ll keep looking to your post for a solution.  regards !!

---

### Post by NEUR0M4NCER on 2007-09-28
I managed to fix the problem, quite simply by doing a fresh install. All worked fine then, until I messed something up, now I can't use anything - fresh post coming up.

---

### Post by rniella on 2007-09-28
just windering... how is it that  you do a fresh install specifically ? run the Live CD and it finds an Ubuntu install and fixes it ??  what happens to all the emails, personal files, etc ?  thanks !!

---

### Post by NEUR0M4NCER on 2007-09-29
Yeah, basically a complete fresh install from the LiveCD. I'm still new to Ubuntu, so most of my important files are still on my Windows partition along with XP Pro, and that's where they're staying until I can get Ubuntu running just the way I want.

---

