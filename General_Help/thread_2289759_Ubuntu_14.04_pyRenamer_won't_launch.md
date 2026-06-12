---
title: "Ubuntu 14.04 pyRenamer won't launch"
date: 2015-08-06
forum: General Help
---

### Post by MyD0j0 on 2015-08-06
I'm running Ubuntu 14.04x64 from a clean install.  Yesterday, I installed pyRenamer using the software center.  When I click the launcher icon in the Unity bar, the icon does it's fancy color gradient to show that it is doing some work, but then stops and pyRenamer never opens.  I've uninstalled and then re-installed.  A cursory glance through the forums and Google search shows no results.

I have been taking a class learning how to program in python (unrelated to why I want pyRenamer) and I do have 2.7.6 and 2.7.10 installed, as well as the default 3.4 that comes bundled with the ubuntu install.  For the 2.7 branch, the interpreter is currently pointed at 2.7.10, but until I finish the class, I can't really uninstall it.  And that's even if multiple versions of python would be the problem.  Anyone know what might be the problem or which log file I should check?

---

### Post by v3.xx on 2015-08-06
Try opening it in terminal
```
pyrenamer
```
Any errors?

---

### Post by MyD0j0 on 2015-08-06
Doh!  It never crossed my mind to do that. ::sheepish grin::  PyGtk 2.0 or better isn't installed.

---

### Post by v3.xx on 2015-08-06
So I'm not the only one :)

---

### Post by MyD0j0 on 2015-08-06
But this is odd... I go to install pygtk and I see in synaptic that python-gtk2 is already installed...?  I looked in there after being told by apt-get that pygtk isn't a package.  Which package is this supposed to be?

```
sudo apt-get build-dep pyrenamer
```

So downloaded the dependencies and are now installed, but 

```
pyrenamer
```

still complains that PyGtk 2.0 or later is still not installed?!?!  What's going on here that I am missing?

---

### Post by MyD0j0 on 2015-08-09
anyone with any thoughts why pyRenamer still complains about pygtk not being installed? 

```

machine ~ $ pyrenamer
PyGtk 2.0 or later required for this app to run
machine ~ $ 

```

```
Python 2.7.6 (default, Jun 22 2015, 17:58:13) [GCC 4.8.2] on linux2
Type "copyright", "credits" or "license()" for more information.
>>> import gtk
>>> gtk.pygtk_version
(2, 24, 0)
>>> 

```

---

