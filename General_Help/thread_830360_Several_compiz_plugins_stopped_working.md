---
title: "Several compiz plugins stopped working"
date: 2008-06-15
forum: General Help
---

### Post by booyabazooka on 2008-06-15
I hit this problem during the transition to Hardy (some time while I was using the beta), and never got around to fixing it until now.

The Negative and Rain plugins don't work.  When they're active, windows just turn solid colors (brown and black for Negative, various blues for Rain).

I know my hardware must support these things, because they were working before.



Results of compiz-check:

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Forlong on 2008-06-17
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by booyabazooka on 2008-06-17
```
ii  compiz                                     1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager
ii  compiz-core                                1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                                     Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                                     Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager - plug
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositi
ii  compizconfig-settings-manager              0.7.4-0ubuntu2                                     Compiz configuration settings manager
ii  emerald                                    0.7.2-0ubuntu2                                     Decorator for compiz-fusion
rc  gnome-compiz-manager                       0.10.3-0ubuntu2                                    Compiz Gnome Manager
ii  libcompizconfig0                           0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.7.2-0ubuntu2                                     Decoration engines for compiz-fusion
rc  libgnome-compiz-manager0                   0.10.3-0ubuntu2                                    Compiz Gnome Manager
ii  python-compizconfig                        0.7.4-0ubuntu1                                     Compiz configuration system bindings

```

---

### Post by Forlong on 2008-06-18
Looks good to me, then it's most probably a settings issue.

You can reset Compiz' settings like this:
```
gconftool-2 --recursive-unset -a /apps/compiz
```
**but you will lose all of your settings then**

---

