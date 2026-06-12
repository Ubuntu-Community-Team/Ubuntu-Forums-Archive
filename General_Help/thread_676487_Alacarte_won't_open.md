---
title: "Alacarte won't open"
date: 2008-01-23
forum: General Help
---

### Post by dbbolton on 2008-01-23
Here is the error I get when I launch alacarte:

```

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: No module named cairo

```I tried to reinstall cairo and python through synaptic, but no dice. "Reinstall" isn't even an option- just remove.

Any ideas?

---

### Post by pointone on 2008-01-23
Try starting a Python interpreter and enter the command: 

```
import cairo
```

If this doesn't work, paste the output of the following command here:

```
locate cairo | grep python
```

---

### Post by dbbolton on 2008-01-23
here is the output:

```

daniel@mephista:~$ python
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import cairo
>>> exit()


daniel@mephista:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: No module named cairo



daniel@mephista:~$ locate cairo | grep python
/usr/lib/python2.4/site-packages/cairo
/usr/lib/python2.4/site-packages/cairo/_cairo.so
/usr/lib/python-support/python-gtk2/python2.4/gtk-2.0/pangocairo.so
/usr/lib/python-support/python-gtk2/python2.5/gtk-2.0/pangocairo.so
/usr/lib/python2.5/site-packages/glchess/scene/cairo
/usr/lib/python2.5/site-packages/glchess/scene/cairo/__init__.py
/usr/lib/python2.5/site-packages/glchess/scene/cairo/pieces.py
/usr/lib/python2.5/site-packages/cairo
/usr/lib/python2.5/site-packages/cairo/__init__.py
/usr/lib/python2.5/site-packages/cairo/_cairo.so
/usr/lib/python2.5/site-packages/cairo/__init__.pyc
/usr/lib/python2.5/site-packages/serpentine/cairopiechart.pyc
/usr/lib/python2.5/site-packages/serpentine/cairopiechart.py
/usr/share/doc/python-gnome2-desktop/examples/rsvg/rsvg-cairo.py
/usr/share/doc/python-cairo-dev
/usr/share/doc/python-cairo-dev/copyright
/usr/share/doc/python-cairo-dev/AUTHORS
/usr/share/doc/python-cairo-dev/NEWS.gz
/usr/share/doc/python-cairo-dev/README
/usr/share/doc/python-cairo-dev/changelog.Debian.gz
/usr/share/doc/python-cairo-dev/changelog.gz
/usr/share/doc/python-cairo
/usr/share/doc/python-cairo/copyright
/usr/share/doc/python-cairo/AUTHORS
/usr/share/doc/python-cairo/examples
/usr/share/doc/python-cairo/examples/hering.py
/usr/share/doc/python-cairo/examples/warpedtext.py
/usr/share/doc/python-cairo/examples/gradient.py
/usr/share/doc/python-cairo/examples/spiral.py
/usr/share/doc/python-cairo/NEWS.gz
/usr/share/doc/python-cairo/README
/usr/share/doc/python-cairo/changelog.Debian.gz
/usr/share/doc/python-cairo/changelog.gz
/var/lib/python-support/python2.5/gtk-2.0/pangocairo.so
/var/lib/dpkg/info/python-cairo-dev.list
/var/lib/dpkg/info/python-cairo.prerm
/var/lib/dpkg/info/python-cairo.postinst
/var/lib/dpkg/info/python-cairo.list
/var/lib/dpkg/info/python-cairo-dev.md5sums
/var/lib/dpkg/info/python-cairo.md5sums

daniel@mephista:~$ 

```

---

### Post by dbbolton on 2008-01-25
Do you know what's causing this?

---

### Post by dbbolton on 2008-01-27
Anyone?

---

### Post by dbbolton on 2008-01-31
This is starting to become a serious problem. Somehow, my custom menu was reset to the default- and of course now I can't edit it whatsoever. Is there some sort of file that I could edit manually?

---

### Post by pointone on 2008-01-31
Try running:

```
python /usr/bin/alacarte
```

---

### Post by dbbolton on 2008-01-31
Eureka! It works perfectly.

Any idea why running 'alacarte' doesn't work?

---

### Post by pointone on 2008-01-31
Please post the output of the following command (finds the shebang line):

```
cat /usr/bin/alacarte | grep /usr/bin/python
```

---

### Post by dbbolton on 2008-01-31
```
#! /usr/bin/python -OOt

```

---

### Post by pointone on 2008-02-01
This has me stumped. The fact that it works when you explicitly run it with "python" indicates some sort of environment mismatch. You haven't changed your default Python install, have you?

Post the output of the command:

```
ls `which python` -l
```

My only other suggestion would be to try disabling the optimizations by editing the /usr/bin/alacarte file and removing the O's. Change it from:

```
#! /usr/bin/python -OOt
```

... to:

```
#! /usr/bin/python -t
```

Other than that, I'm seriously confused.

---

### Post by dbbolton on 2008-02-01
```
lrwxrwxrwx 1 root root 9 2007-05-25 11:57 /usr/bin/python -> python2.5

```

I changed the exec line in the menu item from 'alacarte' to 'python /usr/bin/alacarte' and it seems to work fine, so I probably won't mess with the original bin.

---

