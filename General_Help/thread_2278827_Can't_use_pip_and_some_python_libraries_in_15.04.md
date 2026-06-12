---
title: "Can't use pip and some python libraries in 15.04"
date: 2015-05-19
forum: General Help
---

### Post by Ankush_Menat on 2015-05-19
From last days I am unable to use [python pip]("https://pypi.python.org/pypi/pip"). Pip keeps throwing some errors and I am not able to understand what it means. I reinstalled python, python pip and many other packages, no luck. I can ONLY access pip via sudo su, that too doesn't work for installation or using any apps.
```
sudo su -c "pip"
```

Here's error when I run sudo pip
```
ankush@jarvis:~$ sudo pip
[sudo] password for ankush: 
Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    load_entry_point('pip==1.5.6', 'console_scripts', 'pip')()
  File "/usr/lib/python2.7/dist-packages/pkg_resources/__init__.py", line 521, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python2.7/dist-packages/pkg_resources/__init__.py", line 2632, in load_entry_point
    return ep.load()
  File "/usr/lib/python2.7/dist-packages/pkg_resources/__init__.py", line 2312, in load
    return self.resolve()
  File "/usr/lib/python2.7/dist-packages/pkg_resources/__init__.py", line 2318, in resolve
    module = __import__(self.module_name, fromlist=['__name__'], level=0)
  File "/usr/lib/python2.7/dist-packages/pip/__init__.py", line 74, in <module>
    from pip.vcs import git, mercurial, subversion, bazaar  # noqa
  File "/usr/lib/python2.7/dist-packages/pip/vcs/mercurial.py", line 9, in <module>
    from pip.download import path_to_url
  File "/usr/lib/python2.7/dist-packages/pip/download.py", line 25, in <module>
    from requests.compat import IncompleteRead
ImportError: cannot import name IncompleteRead
```

Here's error when I run python apps installed by pip like [mitmproxy]("https://mitmproxy.org/").
```
ankush@jarvis:~$ sudo mitmproxy 
[sudo] password for ankush: 
Traceback (most recent call last):
  File "/usr/local/bin/mitmproxy", line 2, in <module>
    from libmproxy.main import mitmproxy
  File "/usr/local/lib/python2.7/dist-packages/libmproxy/main.py", line 6, in <module>
    from . import version, cmdline
  File "/usr/local/lib/python2.7/dist-packages/libmproxy/cmdline.py", line 6, in <module>
    from . import filt, utils, version
  File "/usr/local/lib/python2.7/dist-packages/libmproxy/filt.py", line 37, in <module>
    from .protocol.http import decoded
  File "/usr/local/lib/python2.7/dist-packages/libmproxy/protocol/__init__.py", line 1, in <module>
    from .primitives import *
  File "/usr/local/lib/python2.7/dist-packages/libmproxy/protocol/primitives.py", line 4, in <module>
    import netlib.tcp
  File "/usr/local/lib/python2.7/dist-packages/netlib/tcp.py", line 8, in <module>
    from OpenSSL import SSL
  File "/home/ankush/.local/lib/python2.7/site-packages/OpenSSL/__init__.py", line 8, in <module>
    from OpenSSL import rand, crypto, SSL
  File "/home/ankush/.local/lib/python2.7/site-packages/OpenSSL/rand.py", line 11, in <module>
    from OpenSSL._util import (
  File "/home/ankush/.local/lib/python2.7/site-packages/OpenSSL/_util.py", line 6, in <module>
    from cryptography.hazmat.bindings.openssl.binding import Binding
ImportError: No module named cryptography.hazmat.bindings.openssl.binding
```

[IMG]http://i.imgur.com/3CwAGCc.png[/IMG]

---

### Post by dino99 on 2015-05-19
when i glance at python-pip dependencies (from synaptic), it needs  python-setuptools (>=0.6c1), the other dependencies does not have a versioned limit.
These errors you got looks related to a versioning issue. Be sure  about the installed dependencies.

---

### Post by Ankush_Menat on 2015-05-19
> **dino99 said:**
> when i glance at python-pip dependencies (from synaptic), it needs  python-setuptools (>=0.6c1), the other dependencies does not have a versioned limit.
These errors you got looks related to a versioning issue. Be sure  about the installed dependencies.

```
ankush@jarvis:~
$ dpkg -l python-setuptools | grep -E "^ii" | tr -s ' ' | cut -d' ' -f3
12.2-1

```

---

### Post by scott.drake on 2015-06-01
> **Ankush_Menat said:**
> ```
ankush@jarvis:~
$ dpkg -l python-setuptools | grep -E "^ii" | tr -s ' ' | cut -d' ' -f3
12.2-1

```

Known problem: [https://bugs.launchpad.net/ubuntu/+source/python-pip/+bug/1306991](https://bugs.launchpad.net/ubuntu/+source/python-pip/+bug/1306991)

If you don't mind going outside of apt, uninstall python-pip and install it with easy_install:

```
$ sudo apt-get remove python-pip

$ sudo easy_install -U pip
```

Not ideal, but will get you going again.

---

