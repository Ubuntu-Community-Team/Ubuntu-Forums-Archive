---
title: "Problem with installing python, and tcl, and running ap-get upgrade"
date: 2013-11-13
forum: General Help
---

### Post by Maleificus on 2013-11-13
Alright so I tried to install python and tcl today and I got a similar error to the one you are about to see below (the error below is the end of my output of apt-get upgrade) The only thing that has changed on my fresh install of Ubuntu 13.04 recently is having had installed ZNC (the IRC bouncer). Now after having had installed that I tried to compile a module for it and it was giving me an error saying it couldn't find "main.h" (that's not the issue, just giving you background :P) so I was attempting to install the languages that it might need. Now I get the following error when I apt-get upgrade:

> Setting up python2.7-minimal (2.7.4-2ubuntu3.2) ...
# Empty sitecustomize.py to avoid a dangling symlink
Traceback (most recent call last):
  File "/usr/lib/python2.7/py_compile.py", line 170, in <module>
    sys.exit(main())
  File "/usr/lib/python2.7/py_compile.py", line 162, in main
    compile(filename, doraise=True)
  File "/usr/lib/python2.7/py_compile.py", line 106, in compile
    with open(file, 'U') as f:
IOError: [Errno 2] No such file or directory: '/usr/lib/python2.7/sitecustomize.py'
dpkg: error processing python2.7-minimal (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-minimal:
 python-minimal depends on python2.7-minimal (>= 2.7.4-1~); however:
  Package python2.7-minimal is not configured yet.

dpkg: error processing python-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.7:
 python2.7 depends on python2.7-minimal (= 2.7.4-2ubuntu3.2); however:
  Package python2.7-minimal is not configured yet.

dpkg: error processing python2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python:
 python depends on python2.7 (>= 2.7.4-1~); however:
  Package python2.7 is not configured yet.
 python depends on python-minimal (= 2.7.4-0ubuntu1); however:
  Package python-minimal is not configured yet.

dpkg: error processing python (--configure):
 dependency problems - leaving unconfigured
Setting up libapt-inst1.5:i386 (0.9.7.7ubuntu6) ...
Setting up ifupdown (0.7.5ubuntu2.2) ...
Setting up libprocps0:i386 (1:3.3.3-2ubuntu5.3) ...
Setting up libsasl2-2:i386 (2.1.25.dfsg1-6ubuntu0.1) ...
Setting up libwbclient0:i386 (2:3.6.9-1ubuntu1.1) ...
Setting up samba-common (2:3.6.9-1ubuntu1.1) ...
Setting up procps (1:3.3.3-2ubuntu5.3) ...
procps stop/waiting
Setting up samba-common-bin (2:3.6.9-1ubuntu1.1) ...
Setting up samba (2:3.6.9-1ubuntu1.1) ...
Setting up apt-utils (0.9.7.7ubuntu6) ...
Setting up initramfs-tools-bin (0.103ubuntu0.8) ...
Setting up initramfs-tools (0.103ubuntu0.8) ...
update-initramfs: deferring update (trigger activated)
Setting up sasl2-bin (2.1.25.dfsg1-6ubuntu0.1) ...
update-rc.d: warning: saslauthd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 * Starting SASL Authentication Daemon saslauthd                         [ OK ]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
Errors were encountered while processing:
 python2.7-minimal
 python-minimal
 python2.7
 python
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anyone offer any help?

---

### Post by Maleificus on 2013-11-21
Bump

---

### Post by ian-weisser on 2013-11-21
Goodness, how did you manage to get Python 2.7 uninstalled in the first place without completely breaking your system?
Python 2.7 is included by default with every desktop flavor of Ubuntu.

```
Setting up python2.7-minimal (2.7.4-2ubuntu3.2) ...
[COLOR=#ff0000]# Empty sitecustomize.py to avoid a dangling symlink[/COLOR]
Traceback (most recent call last):
  File "/usr/lib/python2.7/py_compile.py", line 170, in <module>
    sys.exit(main())
  File "/usr/lib/python2.7/py_compile.py", line 162, in main
    compile(filename, doraise=True)
  File "/usr/lib/python2.7/py_compile.py", line 106, in compile
    with open(file, 'U') as f:
[COLOR=#ff0000]IOError: [Errno 2] No such file or directory: '/usr/lib/python2.7/sitecustomize.py'[/COLOR]
```
Did you try creating an empty file at /usr/lib/python2.7/sitecustomize.py for the installer to find?

---

### Post by Anyi_Zhu on 2014-03-10
> **ian-weisser said:**
> Goodness, how did you manage to get Python 2.7 uninstalled in the first place without completely breaking your system?
Python 2.7 is included by default with every desktop flavor of Ubuntu.

```
Setting up python2.7-minimal (2.7.4-2ubuntu3.2) ...
[COLOR=#ff0000]# Empty sitecustomize.py to avoid a dangling symlink[/COLOR]
Traceback (most recent call last):
  File "/usr/lib/python2.7/py_compile.py", line 170, in <module>
    sys.exit(main())
  File "/usr/lib/python2.7/py_compile.py", line 162, in main
    compile(filename, doraise=True)
  File "/usr/lib/python2.7/py_compile.py", line 106, in compile
    with open(file, 'U') as f:
[COLOR=#ff0000]IOError: [Errno 2] No such file or directory: '/usr/lib/python2.7/sitecustomize.py'[/COLOR]
```
Did you try creating an empty file at /usr/lib/python2.7/sitecustomize.py for the installer to find?

Worked for me, thanks a lot!

---

