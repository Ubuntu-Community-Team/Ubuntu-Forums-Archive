---
title: "calibre startup error"
date: 2019-05-13
forum: General Help
---

### Post by omerfarukcakmak on 2019-05-13
While calibre is installing I accidentaly closed the terminal on %99 and now when I try to open the calibre, calibre gives this error:

```
calibre, version 3.21.0ERROR: Startup error: There was an error during calibre startup. Parts of calibre may not function. Click Show details to learn more.


Traceback (most recent call last):
  File "/usr/lib/calibre/calibre/gui2/main.py", line 300, in initialize_db_stage2
    self.start_gui(db)
  File "/usr/lib/calibre/calibre/gui2/main.py", line 233, in start_gui
    main = self.main = Main(self.opts, gui_debug=self.gui_debug)
  File "/usr/lib/calibre/calibre/gui2/ui.py", line 156, in __init__
    ac = self.init_iaction(action)
  File "/usr/lib/calibre/calibre/gui2/ui.py", line 170, in init_iaction
    ac = action.load_actual_plugin(self)
  File "/usr/lib/calibre/calibre/customize/__init__.py", line 614, in load_actual_plugin
    ac = getattr(importlib.import_module(mod), cls)(gui,
  File "/usr/lib/python2.7/importlib/__init__.py", line 37, in import_module
    __import__(name)
  File "/usr/lib/calibre/calibre/gui2/actions/catalog.py", line 13, in <module>
    from calibre.gui2.tools import generate_catalog
  File "/usr/lib/calibre/calibre/gui2/tools.py", line 16, in <module>
    from calibre.gui2.convert.single import NoSupportedInputFormats
  File "/usr/lib/calibre/calibre/gui2/convert/single.py", line 20, in <module>
    from calibre.gui2.convert.search_and_replace import SearchAndReplaceWidget
  File "/usr/lib/calibre/calibre/gui2/convert/search_and_replace.py", line 11, in <module>
    from calibre.gui2.convert.search_and_replace_ui import Ui_Form
  File "/usr/lib/calibre/calibre/gui2/convert/search_and_replace_ui.py", line 155, in <module>
    from regex_builder import RegexEdit
  File "/usr/lib/calibre/calibre/gui2/convert/regex_builder.py", line 18, in <module>
    from calibre.ebooks.conversion.search_replace import compile_regular_expression
  File "/usr/lib/calibre/calibre/ebooks/conversion/search_replace.py", line 7, in <module>
    import regex
  File "/usr/lib/python2.7/dist-packages/regex.py", line 389, in <module>
    import _regex_core
  File "/usr/lib/python2.7/dist-packages/_regex_core.py", line 4463, in <module>
    "d": lookup_property(None, "Digit", True),
  File "/usr/lib/python2.7/dist-packages/_regex_core.py", line 1712, in lookup_property
    raise error("unknown property")
error: unknown property



```

I tried purge remove and reinstalling calibre but not worked. How can I fix it?

---

### Post by Impavidus on 2019-05-13
Try```
sudo dpkg --configure -a
sudo apt install -f
```If the latter command proposes to remove a lot of stuff, abort it.

That should finish installation of partially installed packages. Not just calibre, but dependencies as well. At the very least, it should give a more helpful error message.

---

### Post by dragonfly41 on 2019-05-13
There is also calibredb. 

Run command .. ```
calibredb --help
``` for options.

You might have some locked database file. I would backup any such files before tinkering.

```

&#10140;  ~ which calibredb
/usr/bin/calibredb
&#10140;  ~ which calibre
/usr/bin/calibre
&#10140;  ~ 

```

---

