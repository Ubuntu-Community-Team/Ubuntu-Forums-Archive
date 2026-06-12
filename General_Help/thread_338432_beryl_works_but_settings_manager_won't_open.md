---
title: "beryl works but settings manager won't open"
date: 2007-01-14
forum: General Help
---

### Post by m.musashi on 2007-01-14
I have been using beryl more or less trouble free for quite a while. A month or two ago I upgraded to the svn repos and that too was and still is working fine. However, a few days ago I noticed I could not open the settings manager. When I click the icon or try to open from system->preferences->beryl settings nothing would happen. I tried running beryl-settings from a terminal but it returned a segmentation fault error.

I thought an update might help so I ran a general apt-get update and upgrade and beryl still works fine but now beryl-settings is no longer listed under system->preferences, it still won't do anything if I use the gem icon on the panel and if I run it in a terminal I now get this
```
jim@edgy:~$ beryl-settings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in ?
    import berylsettings
ImportError: No module named berylsettings
```
Any thoughts on this? How would I go about fixing /usr/bin/beryl-settings? It's a long file but the first few lines look like
```
#!/usr/bin/env python
import berylsettings
import gtk
import gtk.gdk
import gobject
gdk = gtk.gdk


APP = 'beryl-settings'
DIR = 'locale'
import locale
import gettext
locale.setlocale(locale.LC_ALL, '')
gettext.bindtextdomain(APP, DIR)
gettext.textdomain(APP)
_ = gettext.gettext
```

Or is the error in that berylsettings referenced in line 2 is missing for some reason?

Thanks.

---

### Post by ThrobbingBrain66 on 2007-01-14
I fixed it by installing python2.5 from the repos and then changing the first line of the beryl-settings file to read '#!/usr/bin/python2.5' instead of '#!/usr/bin/env python'

EDIT: First, try to update again, beryl-settings and beryl-settings-bindings updates are available.

---

### Post by m.musashi on 2007-01-14
Thanks. Reinstalling beryl-settings and beryl-settings-bindings fixed it. It looks like they changed the interface again. I guess it's get better each time so that's good.

I didn't install python2.5 so I don't know if I should or not now that it's working again.

Anyway, thanks for the help.

---

### Post by ThrobbingBrain66 on 2007-01-14
> **m.musashi said:**
> Thanks. Reinstalling beryl-settings and beryl-settings-bindings fixed it. It looks like they changed the interface again. I guess it's get better each time so that's good.

I didn't install python2.5 so I don't know if I should or not now that it's working again.

Anyway, thanks for the help.

no need to install python2.5 if everything is working.  I just found that solution on the Beryl forums (before the updates were released) and it worked for me.

---

### Post by m.musashi on 2007-01-14
Thanks. I won't mess with it. I have a bad habit of doing that and end up fixing things a lot :).

Love the avatar by the way. That's the cow bell sketch right? I love that one.

---

