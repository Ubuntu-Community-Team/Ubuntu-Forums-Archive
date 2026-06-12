---
title: "GEdit plugins fail to load."
date: 2007-12-07
forum: General Help
---

### Post by psyguy1 on 2007-12-07
Hi.

I've been using a few GEdit plugins for a while and they worked great.  However, a couple of days ago I installed xfce.  I also updated my gtk and pygtk and installed cairo and pycairo.  (At least, I think I did!)

Now, my plugins won't load anymore.  I get this error:

```
** (gedit:21150): WARNING **: Error, impossible to activate plugin 'Snippets'
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/snippets/__init__.py", line 18, in ?
    import gedit
ImportError: No module named gedit

** (gedit:21150): WARNING **: Could not load python module snippets
```

If I make a plugin that does nothing more than print "Hello world" to the console, I still get this error.

```
** (gedit:21150): WARNING **: Could not load python module RunInPython


** (gedit:21150): WARNING **: Error, impossible to activate plugin 'Run In Python'
```

While searching on this problem over the last couple of days, I saw someone suggest (to someone who had a similar problem) running this command and posting its output.

```
mike@mike-desktop:~/Desktop/gtk+-2.10.14$ dpkg -l 'py*gtk*' | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name               Version         Description
+++-==================-===============-============================================
un  python-gtk         <none>          (no description available)
ii  python-gtk-1.2     0.6.12-7        GTK support module for Python
ii  python-gtk2        2.10.3-0ubuntu3 Python bindings for the GTK+ widget set
pn  python-gtk2-dev    <none>          (no description available)
pn  python-gtkhtml2    <none>          (no description available)
un  python-wxgtk2.4    <none>          (no description available)
ii  python-wxgtk2.6    2.6.3.2.1.5     wxWidgets Cross-platform C++ GUI toolkit (wx
un  python2.2-gtk2     <none>          (no description available)
un  python2.3-gtk2     <none>          (no description available)
un  python2.4-gtk2     <none>          (no description available)
un  python2.4-wxgtk2.6 <none>          (no description available)
un  python2.5-gtk2     <none>          (no description available)
```

Unfortunately they never followed up on the suggestion, so I don't know what to interpret from the results.

Can some please help me track down what is causing this problem?  Ubuntu treats me pretty well but this is something I just haven't been able to figure out.

Thanks!  :)

[i]Edit - Oh, and I think this is a little relevant also.  When I try to import gtk from the python console, it gives this error:

```
>>> import gtk
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "/var/lib/python-support/python2.4/gtk-2.0/gtk/__init__.py", line 48, in ?
    from gtk import _gtk
  File "/usr/local/lib/python2.4/site-packages/cairo/__init__.py", line 1, in ?
    from _cairo import *
ImportError: /usr/local/lib/python2.4/site-packages/cairo/_cairo.so: undefined symbol: cairo_copy_clip_rectangle_list
```[/i]

---

