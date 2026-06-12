---
title: "Help getting LIOS OCR working again"
date: 2024-06-03
forum: General Help
---

### Post by pedro_rodriguez2 on 2024-06-03
Hi, I was a great fan of LIOS OCR. A while ago it stopped working. I would love to get LIOS working again. I saw a thread here about trying to check the Python.

I use Ubuntu 22.04 and Python 3.10

Can someone please tell how I might fix this error in bash?

> pedro@pedro-HP:/usr/lib/python3/dist-packages/gi$ lios
/usr/lib/python3/dist-packages/lios/ui/gtk/text_view.py:21: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
/usr/lib/python3/dist-packages/lios/ui/gtk/widget.py:24: PyGIWarning: Atk was imported without specifying a version first. Use gi.require_version('Atk', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Atk
Traceback (most recent call last):
  File "/usr/bin/lios", line 3, in <module>
    from lios.main import *
  File "/usr/lib/python3/dist-packages/lios/main.py", line 27, in <module>
    from lios import scanner, editor, imageview, cam, ocr, preferences, speech, train_tesseract
  File "/usr/lib/python3/dist-packages/lios/editor.py", line 20, in <module>
    from lios.ui.gtk import text_view, tree_view, widget, dialog, file_chooser, containers, window
  File "/usr/lib/python3/dist-packages/lios/ui/gtk/widget.py", line 166, in <module>
    class Separator(Gtk.HSeparator):
  File "/usr/lib/python3/dist-packages/gi/overrides/__init__.py", line 32, in __getattr__
    return getattr(self._introspection_module, name)
  File "/usr/lib/python3/dist-packages/gi/module.py", line 123, in __getattr__
    raise AttributeError("%r object has no attribute %r" % (
AttributeError: 'gi.repository.Gtk' object has no attribute 'HSeparator'
pedro@pedro-HP:/usr/lib/python3/dist-packages/gi$ 


---

### Post by dragonfly41 on 2024-06-03
The clue is emedded in your log above.

[COLOR=#000000][I]```
Use gi.require_version('Gtk', '4.0') before import to ensure that the right version gets loaded.
```

[/I]So it seems that LIOS is using an early version of Gtk.

You could try hacking the Python files referred to but I have no experience with this app. I just happen to be interested in OCR so tried it myself out of curiosity.

Others suggest using tesseract.[/COLOR]

---

### Post by currentshaft on 2024-06-03
I would use miniconda to set up an environment with an earlier, compatible version of Python to run this tool.

---

### Post by Holger_Gehrke on 2024-06-03
The author of Lios has a PPA. Seems like the version in the PPA is actually newer than the one on Github and it starts without any problems on my Xubuntu 22.04 system. Search for nalin-x-linux on launchpad.

Holger

---

### Post by pedro_rodriguez2 on 2024-06-03
Think I narrowed it down a bit. 

File "/usr/lib/python3/dist-packages/lios/ui/gtk/widget.py", line 166, in <module>

In widget.py is this class is on line 166:

```
class Separator(Gtk.HSeparator):
    def __init__(self):
        super(Separator,self).__init__()
```

Causing this error:

> pedro@pedro-HP:/usr/lib/python3/dist-packages/gi$ lios
Traceback (most recent call last):
  File "/usr/bin/lios", line 3, in <module>
    from lios.main import *
  File "/usr/lib/python3/dist-packages/lios/main.py", line 27, in <module>
    from lios import scanner, editor, imageview, cam, ocr, preferences, speech, train_tesseract
  File "/usr/lib/python3/dist-packages/lios/editor.py", line 20, in <module>
    from lios.ui.gtk import text_view, tree_view, widget, dialog, file_chooser, containers, window
  **File "/usr/lib/python3/dist-packages/lios/ui/gtk/widget.py", line 166, in <module>**
    class Separator(Gtk.HSeparator):
  File "/usr/lib/python3/dist-packages/gi/overrides/__init__.py", line 32, in __getattr__
    return getattr(self._introspection_module, name)
  File "/usr/lib/python3/dist-packages/gi/module.py", line 123, in __getattr__
    raise AttributeError("%r object has no attribute %r" % (
**AttributeError: 'gi.repository.Gtk' object has no attribute 'HSeparator'**


Following a [link to Gtk]("https://docs.gtk.org/gtk3/ctor.HSeparator.new.html")
I tried replacing Gtk.HSeparator with Gtk.gtk_hseparator_new in the class, but just get a similar error:

> **AttributeError: 'gi.repository.Gtk' object has no attribute 'gtk_hseparator_new'**


Anyone know what it should be??

---

### Post by pedro_rodriguez2 on 2024-06-04
Thanks for your replies!

following Holger_Gehrke's suggestion, I added the PPA and installed LIOS fron there. Now LIOS works!

LIOS seems to require Gtk 3.0

I still got this error in bash when I started LIOS, although LIOS did start and work.

> pedro@pedro-HP:~$ lios
/usr/lib/python3/dist-packages/lios/ui/gtk/print_dialog.py:26: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import PangoCairo


(lios:5562): Gtk-WARNING **: 06:13:35.786: Cannot connect attribute 'text' for cell renderer class 'lios+ui+gtk+tree_view+CellRendererToggle' since attribute does not exist


Using this command I edited print_dialog.py

> pedro@pedro-HP:~$ gedit admin:///usr/lib/python3/dist-packages/lios/ui/gtk/print_dialog.py

Now, print-dialog.py has this at the top:

> import gi
gi.require_version("Gtk", "3.0")
gi.require_version('PangoCairo', '1.0')


I still get this error in bash, but I can OCR using LIOS again!

> pedro@pedro-HP:~$ lios


(lios:6417): Gtk-WARNING **: 06:23:17.073: Cannot connect attribute 'text' for cell renderer class 'lios+ui+gtk+tree_view+CellRendererToggle' since attribute does not exist
pedro@pedro-HP:~$ 




Also, LIOS keeps asking me to install aspell-chi_sim on starting, but, it seems this package does not exist:

> pedro@pedro-HP:~$ sudo apt install aspell-chi_sim
[sudo] password for pedro: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package aspell-chi_sim

tesseract has chi_sim and I can OCR Chinese text successfully, so I am not sure why I need aspell-chi_sim.

---

