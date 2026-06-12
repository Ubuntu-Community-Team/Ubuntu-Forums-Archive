---
title: "I killed my compiz.."
date: 2008-05-29
forum: General Help
---

### Post by bakersfield90 on 2008-05-29
I recently tried to install via the Add/Remove list "Advanced Desktop Effects Settings (ccsm)".

When the installation completed I tried to open up the program. The program refused to open after several tries and I decided to give up and uninstall the program.

Upon uninstalling, the desktop effects would not work, and several of my keyboard shortcuts would not work.

I could use some help.
Rather than reinstalling, I am clueless what to do.

NOTE: I am running 7.10

---

### Post by cubeist on 2008-05-30
The best place to start is to install ccsm again, then try starting it from the terminal (just type ccsm and hit return).  Watch for error messages and post back!

---

### Post by bakersfield90 on 2008-05-30
> **cubeist said:**
> The best place to start is to install ccsm again, then try starting it from the terminal (just type ccsm and hit return).  Watch for error messages and post back!
```

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
```

---

### Post by Forlong on 2008-05-30
Post the output of ```
dpkg -l | grep compiz
```

---

### Post by bakersfield90 on 2008-05-30
> **Forlong said:**
> Post the output of ```
dpkg -l | grep compiz
```

```
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0        Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0         GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
```

---

### Post by Forlong on 2008-05-31
> ```
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0        Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0         GNOME Backend for the Compiz Configuration S
```
You have a repository not suitable for your version of Ubuntu enabled.

Go to *System &#8594; Administration &#8594; Software Sources* and remove any third party software sources you added there that might be related.
Afterwards, remove all Compiz packages from your system.
Do a
```
sudo apt-get update
```
And finally install Compiz again.

---

### Post by bakersfield90 on 2008-05-31
[[IMG]http://img231.imageshack.us/img231/9340/screenshot1hf8.png[/IMG]](http://imageshack.us)

now it opens, but I get that.

---

### Post by Tehathu on 2008-05-31
this is where i usually backup and reformat and and reinstall, I tend to just nuke it at the first sign of trouble.

Tehathu

---

### Post by bakersfield90 on 2008-05-31
> **Tehathu said:**
> this is where i usually backup and reformat and and reinstall, I tend to just nuke it at the first sign of trouble.

Tehathu

yeah... same here but i'm on my 6th or 7th install in under 2 months.. and i just got everything working except for this. maybe i should reinstall and never mess with compiz again?

---

### Post by Forlong on 2008-05-31
> **bakersfield90 said:**
> now it opens, but I get that.
Post the output of ```
dpkg -l | grep compiz
``` again.

---

