---
title: "Python-minimal failing to install while upgrading to latest Ubuntu?"
date: 2016-08-07
forum: General Help
---

### Post by umrashrf89 on 2016-08-07
I have same problem.

```
$ sudo dpkg --configure -a

Errors were encountered while processing:
 python-dev
 python-gobject-2-dev
 python-minimal
 python-all-dev
 python-gtk2-dev
 python-all
 python-support
```

Different versions of dependencies seems to be a problem.

```
$ sudo apt-get install python-minimal

The following packages have unmet dependencies:
python : Depends: python-minimal (= 2.7.5-5ubuntu3) but 2.7.11-1 is installed
Depends: libpython-stdlib (= 2.7.5-5ubuntu3) but 2.7.11-1 is installed
python-all : Depends: python (= 2.7.11-1) but 2.7.5-5ubuntu3 is installed
python-all-dev : Depends: python (= 2.7.11-1) but 2.7.5-5ubuntu3 is installed
python-dev : Depends: python (= 2.7.11-1) but 2.7.5-5ubuntu3 is installed
```

Any idea how to fix this?

---

### Post by umrashrf89 on 2016-08-07
[SIZE=5]The root cause seems to be python-minimal is failing to be installed.[/SIZE]

```
Setting up python-minimal (2.7.11-1) ...
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/runpy.py", line 162, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/local/lib/python2.7/runpy.py", line 72, in _run_code
    exec code in run_globals
  File "/usr/local/lib/python2.7/compileall.py", line 16, in <module>
    import struct
  File "/usr/local/lib/python2.7/struct.py", line 1, in <module>
    from _struct import *
ImportError: No module named _struct
dpkg: error processing package python-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by JLH02 on 2016-08-09
I ran into the same issue.  The thread at this link was helpful: [https://ubuntuforums.org/showthread.php?t=2321861&page=2&p=13529015#post13529015](https://ubuntuforums.org/showthread.php?t=2321861&page=2&p=13529015#post13529015)

To summarize, try running [COLOR=#000000]`sudo python2.7 -m compileall /usr/share/python/` in order to identify what is causing the error.  Delete/move the offending files, then run [/COLOR][COLOR=#000000]`sudo apt-get install -f`.

In my case, a version of GNS3 that I had installed from source was causing the issues.  

EX:
[/COLOR]```
Compiling /usr/share/python/gns3-gui/lib/python3.4/site-packages/gns3/main.py ...
  File "/usr/share/python/gns3-gui/lib/python3.4/site-packages/gns3/main.py", line 130
    print("".join(lines), file=sys.stderr)
                              ^
SyntaxError: invalid syntax
```

---

### Post by umrashrf89 on 2016-08-12
Thanks for your comments. Today I got time to look into this.

I did the same thing to debug as you and changing post installation script of python-minimal fixed it for me.

```
$  cat /var/lib/dpkg/info/python-minimal.postinst
#! /bin/sh
set -e


python2.7 -m compileall /usr/share/python/ >/dev/null
```

[SIZE=7]TO[/SIZE]

```
$  cat /var/lib/dpkg/info/python-minimal.postinst
#! /bin/sh
set -e


python -m compileall /usr/share/python/ >/dev/null
```

---

### Post by vilvo on 2017-01-20
> **umrashrf89 said:**
> 
.. changing post installation script of python-minimal fixed it for me.


Thank you. This enabled also me to reinstall my broken python in 16.04.

---

### Post by marc.torrellas on 2017-11-20
Thanks! it worked for me

---

### Post by richansah on 2018-08-18
> **umrashrf89 said:**
> Thanks for your comments. Today I got time to look into this.

I did the same thing to debug as you and changing post installation script of python-minimal fixed it for me.

```
$  cat /var/lib/dpkg/info/python-minimal.postinst
#! /bin/sh
set -e


python2.7 -m compileall /usr/share/python/ >/dev/null
```

[SIZE=7]TO[/SIZE]

```
$  cat /var/lib/dpkg/info/python-minimal.postinst
#! /bin/sh
set -e


python -m compileall /usr/share/python/ >/dev/null
```

This helped... Thanks

---

