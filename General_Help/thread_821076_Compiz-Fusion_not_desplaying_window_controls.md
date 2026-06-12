---
title: "Compiz-Fusion not desplaying window controls"
date: 2008-06-06
forum: General Help
---

### Post by [Rolamoto] on 2008-06-06
I recently installed Ubuntu 8.04 on my PowerMac G4 ad got Compiz-Fusion working. However, when I start it, the window controls don't show up. Can anyone help?

---

### Post by Forlong on 2008-06-07
What happens when running
```
gtk-window-decorator --replace
``` in terminal?

---

### Post by [Rolamoto] on 2008-06-07
> **Forlong said:**
> What happens when running
```
gtk-window-decorator --replace
``` in terminal?

Nothing.

---

### Post by Forlong on 2008-06-07
Is Compiz running at all?
What's the output when running ```
compiz
``` in a terminal?

---

### Post by [Rolamoto] on 2008-06-07
> **Forlong said:**
> Is Compiz running at all?
What's the output when running ```
compiz
``` in a terminal?

It returned ```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 0000:00:10.0 0300: 1002:5157 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (512): Failed.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: no 'core' plugin with ABI version '20071103' loaded

/usr/bin/compiz.real (ccp) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

```

---

### Post by Forlong on 2008-06-07
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by [Rolamoto] on 2008-06-07
```

ii  compiz                                     1:0.7.4-0ubuntu6                    OpenGL window and compositing manager
ii  compiz-core                                1:0.7.4-0ubuntu6                    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                1:0.6.0+git20071115+aantngutsy0.2   Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 1:0.6.0+git20071115+aantngutsy0.2   Collection of Compiz Fusion plugins for Comp
ii  compiz-gnome                               1:0.7.4-0ubuntu6                    OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.7.4-0ubuntu6                    OpenGL window and compositing manager - plug
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                      Settings library for plugins - OpenCompositi
ii  compizconfig-settings-manager              1:0.6.0+git20071115+aantngutsy0.2   Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig0                           1:0.6.0+git20071106+aantngutsy0.3   Settings library for plugins - Compiz Fusion
ii  python-compizconfig                        1:0.6.0+git20071106+aantngutsy0.3   Python bindings for the Compiz Configuration

```

---

### Post by Forlong on 2008-06-07
As you can see, you have still 3rd party gutsy packages installed.
Remove the 3rd party repository and remove all Compiz packages you have installed.
Then reload apt via Synaptic or 'sudo apt-get update' and install Compiz again.

---

### Post by [Rolamoto] on 2008-06-07
Thanks, that works like a charm.

---

