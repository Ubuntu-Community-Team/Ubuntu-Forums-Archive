---
title: "Barely any commands work, no module named 'apt_pkg'"
date: 2020-02-20
forum: General Help
---

### Post by retsek2 on 2020-02-20
I don't know what I've done but basic commands like "ls" and "sudo" no longer work and now throw me this error message.

```
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 28, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 19, in <module>
    from CommandNotFound.db.db import SqliteDatabase
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/db.py", line 5, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 24, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
```

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 28, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 19, in <module>
    from CommandNotFound.db.db import SqliteDatabase
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/db.py", line 5, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'

---

### Post by guiverc on 2020-02-20
My guess from your copy/paste is you've changed the default `python3` version to be something different to what your release default should be, thus Ubuntu tools that use `python3` will no longer function.  I'd reverse that (and command `history` should remind you).

That shouldn't impact `ls` or anything that isn't reliant on `python3` so maybe you've made `alias` or other changes to your terminal shell defaults; where I'd view your command `history` expecting to see a `vim ~/.bash...` like command telling me where to look for the problem I created - if I was in your shoes.

This is opinion only (*using code tags makes it more readable and your paste isn't easy to read*)

---

### Post by retsek2 on 2020-02-20
Those are both things that I have done lmao great detective work.
Also I tried to use code tags I apologise I didn't realise it didn't work. I have gotten rid of my aliases and path edits now :)

---

