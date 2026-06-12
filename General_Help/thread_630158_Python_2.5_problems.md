---
title: "Python 2.5 problems"
date: 2007-12-03
forum: General Help
---

### Post by Devoid on 2007-12-03
ok i am also having problems with python 2.5.  I just installed it and its not finding module gobject...  how can i fix this?  im trying to install the new version of nicotine+ and am having no luck in fixing this myself.  PLEASE HELP!!!

root@Satan:/home/devoid/Downloads/nicotine+-1.2.9# python setup.py install
Traceback (most recent call last):
  File "setup.py", line 48, in <module>
    from pynicotine.utils import version
  File "/home/devoid/Downloads/nicotine+-1.2.9/pynicotine/utils.py", line 33, in <module>
    import gobject
ImportError: No module named gobject

ok i reinstaled a bunch of the gtk and gobject libs and devs, and python and im still getting the same errors

i cant think anymore someone help!

does no one know what i can do?

---

