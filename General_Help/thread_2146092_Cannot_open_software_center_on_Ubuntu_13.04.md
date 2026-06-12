---
title: "Cannot open software center on Ubuntu 13.04"
date: 2013-05-17
forum: General Help
---

### Post by apastuszak on 2013-05-17
when I launch it from the terminal, here is what I get:

File "/usr/bin/software-center", line 36, in <module>
    from softwarecenter.utils import (
  File "/usr/share/software-center/softwarecenter/utils.py", line 48, in <module>
    from config import get_config
  File "/usr/share/software-center/softwarecenter/config.py", line 33, in <module>
    class SoftwareCenterConfig(object, SafeConfigParser):
  File "/usr/lib/python2.7/abc.py", line 87, in __new__
    cls = super(ABCMeta, mcls).__new__(mcls, name, bases, namespace)
TypeError: Error when calling the metaclass bases
    Cannot create a consistent method resolution
order (MRO) for bases object, SafeConfigParser


I have tried to reinstall it fromSynaptic.  Same error.

---

### Post by fantab on 2013-05-17
Try:

sudo apt-get install software-center --reinstall

---

### Post by apastuszak on 2013-05-17
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
    from debfile import DebFileApplication, DebFileOpenError
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
    from softwarecenter.db.application import Application, AppDetails
  File "/usr/share/software-center/softwarecenter/db/application.py", line 28, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 26, in <module>
    from softwarecenter.utils import UnimplementedError, utf8
  File "/usr/share/software-center/softwarecenter/utils.py", line 48, in <module>
    from config import get_config
  File "/usr/share/software-center/softwarecenter/config.py", line 33, in <module>
    class SoftwareCenterConfig(object, SafeConfigParser):
  File "/usr/lib/python2.7/abc.py", line 87, in __new__
    cls = super(ABCMeta, mcls).__new__(mcls, name, bases, namespace)
TypeError: Error when calling the metaclass bases
    Cannot create a consistent method resolution
order (MRO) for bases object, SafeConfigParser
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 38, in <module>
    from softwarecenter.db.update import rebuild_database
  File "/usr/share/software-center/softwarecenter/db/update.py", line 33, in <module>
    from softwarecenter.backend.scagent import SoftwareCenterAgent
  File "/usr/share/software-center/softwarecenter/backend/scagent.py", line 28, in <module>
    from softwarecenter.distro import get_distro, get_current_arch
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 26, in <module>
    from softwarecenter.utils import UnimplementedError, utf8
  File "/usr/share/software-center/softwarecenter/utils.py", line 48, in <module>
    from config import get_config
  File "/usr/share/software-center/softwarecenter/config.py", line 33, in <module>
    class SoftwareCenterConfig(object, SafeConfigParser):
  File "/usr/lib/python2.7/abc.py", line 87, in __new__
    cls = super(ABCMeta, mcls).__new__(mcls, name, bases, namespace)
TypeError: Error when calling the metaclass bases
    Cannot create a consistent method resolution
order (MRO) for bases object, SafeConfigParser

---

### Post by apastuszak on 2013-05-17
Here is the fix:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1038429/comments/3](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1038429/comments/3)

---

