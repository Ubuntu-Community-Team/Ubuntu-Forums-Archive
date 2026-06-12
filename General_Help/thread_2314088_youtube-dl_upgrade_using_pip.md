---
title: "youtube-dl upgrade using pip"
date: 2016-02-18
forum: General Help
---

### Post by mbnoimi on 2016-02-18
I'm unable to upgrade youtube-dl using pip. How can I fix the following issue?

```
#  pip install youtube-dl --upgrade
Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    load_entry_point('pip==1.5.4', 'console_scripts', 'pip')()
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 351, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2363, in load_entry_point
    return ep.load()
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2088, in load
    entry = __import__(self.module_name, globals(),globals(), ['__name__'])
  File "/usr/local/lib/python2.7/dist-packages/pip/__init__.py", line 13, in <module>
    from pip.utils import get_installed_distributions, get_prog
ImportError: No module named utils

```

---

### Post by bapoumba on 2016-02-19
Sorry, thread closed, please see here : [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

---

