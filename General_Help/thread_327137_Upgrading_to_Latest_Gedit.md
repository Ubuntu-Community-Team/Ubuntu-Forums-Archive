---
title: "Upgrading to Latest Gedit"
date: 2006-12-28
forum: General Help
---

### Post by EReckase on 2006-12-28
I was going to install the latest version of gedit to try to get rid of some of the startup/execution warnings (I do a lot of work in the terminal while running gedit, so it messes up my window - plus I just don't like warnings), but when I tried to uninstall the existing version (2.14.4, for Ubuntu Dapper) it tells me that I have to uninstall 'ubuntu-desktop' - and I'm not about to do that.  Should I just install to a different location and remove/rename the executable in /usr/bin?

---

### Post by melancholeric on 2006-12-28
As far as I know "ubuntu-desktop" is a metapackage that just contains the dependencies and it should be possible to remove that with apt-get or synaptic without actually removing the desktop. I removed it too when I removed unnecessary accessibility functions and screensavers.

---

### Post by engla on 2006-12-28
Well, I'd like to say this that there are no shortcuts to some things. 

Gedit is an example; it's very tightly integrated with gnome, so for example gedit v2.16 requires gtk 2.10 (dapper has 2.8) etc etc so there is lots and lots of work to do to put it on dapper. You can't just upgrade the gedit package by itself.

The no shortcuts thing means that; gedit 2.16 is part of the larger Gnome 2.16 package and it is only available in Ubuntu 6.10. It is in itself, just like the rest of 6.10 _unstable_. There is no shortcut to this particular thing.

Look into backports. They backport things, but if you look at what they deal with it's only the packages  that can be replaced one-by-one and are not too deeply integrated (like firefox can't be backported).

That said, it should be possible to build and install all the needed things in parallell to your current system, but it will be quite a lot of libraries.

---

### Post by EReckase on 2006-12-29
...well, in that case, is there any way that I can get the warnings to go away?  I keep getting:

```
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'
** (gedit:3125): WARNING **: Could not load python module modelines
** (gedit:3125): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed
** (gedit:3125): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

```

...and regular repetitions of the GEDIT_IS_PLUGIN message.  I've only read one or two potential solutions to this, and I've definitely got gtksourceview installed, so I'm not sure what to do next.

Thanks.

---

