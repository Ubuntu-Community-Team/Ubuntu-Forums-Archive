---
title: "AppImage (Vidcutter) not running"
date: 2017-07-08
forum: General Help
---

### Post by maglin2 on 2017-07-08
I'm hoping for some help in getting an AppImage to run. I have made it executable, and when I try to run it from dash there is a hopeful looking whirring cursor, and an icon appears in the launcher sidebar, but then nothing else and the icon eventually disappears.

Trying to run it in terminal I get
```
dave@dave-Aspire-7736:~$ /home/dave/Documents/VidCutter-3.5.0-linux-x64.AppImage/bin/bash: /tmp/.mount_WybIyw/lib/x86_64-linux-gnu/libtinfo.so.5: no version information available (required by /bin/bash)
Traceback (most recent call last):
  File "/tmp/.mount_WybIyw/usr/bin/vidcutter", line 16, in <module>
    sys.exit(load_entry_point('vidcutter', 'gui_scripts', 'vidcutter')())
  File "/usr/lib/python3/dist-packages/pkg_resources.py", line 351, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python3/dist-packages/pkg_resources.py", line 2363, in load_entry_point
    return ep.load()
  File "/usr/lib/python3/dist-packages/pkg_resources.py", line 2088, in load
    entry = __import__(self.module_name, globals(),globals(), ['__name__'])
  File "/usr/lib/python3/dist-packages/vidcutter/__main__.py", line 33, in <module>
    from PyQt5.QtCore import (QCommandLineOption, QCommandLineParser, QDir, QFileInfo, QProcess,
ImportError: No module named 'PyQt5.QtCore'
dave@dave-Aspire-7736:~$
``` 

I couldn't find a module called 'PyQt5.QtCore', but I did find and install package python-pyqt5 and python3-pyqt5 which apparently contain QtCore, however nothing has changed.

---

### Post by TheFu on 2017-07-08
I had a similar issue a few months ago.  Don't remember if it was that exact one or not.  
I opened an issue on the vidcutter site.  A few days later, there was a new vidcutter release that solved it.

---

### Post by maglin2 on 2017-07-08
Thanks - I'm trying 3.5.0 which is stated as being the latest release (29th May).

I assume you have it running under Lubuntu (as opposed to Unity)?

Edit - just found this, which I think may possibly be the issue - will be fixed in the next release I think (hope).
[https://github.com/ozmartian/vidcutter/commit/5bfd5517c229e23662c6357b0f354679ff6062f2](https://github.com/ozmartian/vidcutter/commit/5bfd5517c229e23662c6357b0f354679ff6062f2)

---

### Post by maglin2 on 2017-07-09
I'm marking this solved. It seems to be either an Ubuntu bug or a Vidcutter bug, and not likely amenable to resolution through forum support.

---

### Post by TheFu on 2017-07-09
> **maglin2 said:**
> I'm marking this solved. It seems to be either an Ubuntu bug or a Vidcutter bug, and not likely amenable to resolution through forum support.

If I had to guess, I'd say 90% chance of vidcutter issue (probably packaging) and 10% chance of Ubuntu issue.

---

