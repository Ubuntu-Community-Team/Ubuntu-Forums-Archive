---
title: "Anyone familiar with CKAN data portal?"
date: 2013-06-15
forum: General Help
---

### Post by nellolikejello on 2013-06-15
If you're not familiar with CKAN, check out their [website]("http://ckan.org"). It's an open source data portal and data management solution.

I'm trying to intsall CKAN on Ubuntu 13.04, but keep getting one annoying traceback error:[INDENT]
[FONT=courier new]Traceback (most recent call last):
  File "/usr/bin/ckan", line 4, in <module>
    from pkg_resources import load_entry_point
  File  "/usr/lib/ckan/default/local/lib/python2.7/site-packages/distribute-0.6.24-py2.7.egg/pkg_resources.py",  line 16, in <module>
    import sys, os, zipimport, time, re, imp, types
  File "/usr/lib/ckan/default/lib/python2.7/re.py", line 105, in <module>
    import sre_compile
  File "/usr/lib/ckan/default/lib/python2.7/sre_compile.py", line 14, in <module>
    import sre_parse
  File "/usr/lib/ckan/default/lib/python2.7/sre_parse.py", line 17, in <module>
    from sre_constants import *
  File "/usr/lib/ckan/default/lib/python2.7/sre_constants.py", line 18, in <module>
    from _sre import MAXREPEAT
ImportError: cannot import name MAXREPEAT[/FONT]
[/INDENT]

Anyone familar with this error message? Your help is much appreciated.

---

