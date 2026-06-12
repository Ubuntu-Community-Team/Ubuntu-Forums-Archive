---
title: "Tux Droid Python problem"
date: 2008-04-25
forum: General Help
---

### Post by midnightray on 2008-04-25
Just got my Tux Droid and plugged it in. The "tuxgdg" gives errors when run. Followed advice of installing "python-xml" but this doesn't fix it!

Anyone good with python / fixed this bug in another application before?

```
Traceback (most recent call last):
  File "/opt/tuxdroid/apps/tux_framework/TFW.py", line 12, in <module>
    from FWObject import GdgFramework
  File "/opt/tuxdroid/apps/tux_framework/libs/FWObject.py", line 35, in <module>
    from GdgObject import *
  File "/opt/tuxdroid/apps/tux_framework/libs/GdgObject.py", line 38, in <module>
    from TGFormat import *
  File "/opt/tuxdroid/apps/tux_framework/libs/TGFormat.py", line 30, in <module>
    from TGFXml import *
  File "/opt/tuxdroid/apps/tux_framework/libs/TGFXml.py", line 26, in <module>
    import xml.dom.ext
ImportError: No module named ext

```

---

