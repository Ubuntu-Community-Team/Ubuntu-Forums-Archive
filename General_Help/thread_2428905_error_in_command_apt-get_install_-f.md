---
title: "error in command apt-get install -f"
date: 2019-10-10
forum: General Help
---

### Post by russell-li on 2019-10-10
I can not update software in Gear Software Manager, and it returned error:[COLOR=#333333][FONT=Arial]dependency broken
[/FONT][/COLOR]so i run the command apt-get install -f, but it return other error:
```
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ModuleNotFoundError: No module named 'ConfigParser'
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
```
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ModuleNotFoundError: No module named 'ConfigParser'
dpkg: &#22788;&#29702;&#36719;&#20214;&#21253; python-cryptography (--configure)&#26102;&#20986;&#38169;&#65306;
 installed python-cryptography package post-installation script subprocess returned error exit status 1
&#27491;&#22312;&#35774;&#32622; python-pip (9.0.1-2.3~ubuntu1.18.04.1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ModuleNotFoundError: No module named 'ConfigParser'
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
```
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ModuleNotFoundError: No module named 'ConfigParser'
dpkg: &#22788;&#29702;&#36719;&#20214;&#21253; python-pip (--configure)&#26102;&#20986;&#38169;&#65306;
 installed python-pip package post-installation script subprocess returned error exit status 1
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; man-db (2.8.3-2ubuntu0.1) &#30340;&#35302;&#21457;&#22120; ...
&#22312;&#22788;&#29702;&#26102;&#26377;&#38169;&#35823;&#21457;&#29983;&#65306;
 python-gi
 python-cryptography
 python-pip
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can anyone help me? Thanks!

---

### Post by cruzer001 on 2019-10-10
I did a quick read on Gear Software Manager and it seems to be for Android.

What are you running this on?  From where did you download?  And last, what are you running?  Ubuntu? 18.04?

---

### Post by GhX6GZMB on 2019-10-11
Never heard of Gear Software Manager for Ubuntu. I strongly suggest that you use the tools supplied with the installation instead of dubious software.

---

