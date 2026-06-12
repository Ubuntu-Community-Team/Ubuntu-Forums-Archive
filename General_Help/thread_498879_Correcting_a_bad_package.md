---
title: "Correcting a bad package"
date: 2007-07-11
forum: General Help
---

### Post by ddollas on 2007-07-11
I have a bad python-uno package and it is now preventing me from upgrading my system at all.  I don't know how to remove it or correct this issue.  I tried to purge it but it informed me that the package is in a bad shape and should be reinstalled before removing.  When I attempt to install the package again I get this error.  I apologize for the error being large.  

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python-uno
1 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
5 not fully installed or removed.
Need to get 0B/1550kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 109134 files and directories currently installed.)
Preparing to replace update-manager-core 1:0.59.20 (using .../update-manager-core_1%3a0.59.20_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 954, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 954, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: error processing /var/cache/apt/archives/update-manager-core_1%3a0.59.20_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 878, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace gnome-app-install 0.3.30 (using .../gnome-app-install_0.3.30_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 954, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 954, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: error processing /var/cache/apt/archives/gnome-app-install_0.3.30_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 878, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Selecting previously deselected package python-uno.
Preparing to replace python-uno 2.2.0-1ubuntu3 (using .../python-uno_2.2.0-1ubuntu4_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 954, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 954, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: error processing /var/cache/apt/archives/python-uno_2.2.0-1ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 878, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace update-manager 1:0.59.20 (using .../update-manager_1%3a0.59.20_all.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 954, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 954, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.59.20_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 878, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 320, in read_pyfiles
    lines = [s[:-1] for s in fd.readlines()]
IOError: [Errno 14] Bad address
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager-core_1%3a0.59.20_i386.deb
 /var/cache/apt/archives/gnome-app-install_0.3.30_all.deb
 /var/cache/apt/archives/python-uno_2.2.0-1ubuntu4_i386.deb
 /var/cache/apt/archives/update-manager_1%3a0.59.20_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I tried to fix broken packages in synaptic, that also didn't seem to help.  Any suggestions?

---

### Post by solar george on 2007-07-12
This is just an idea but it may work,

Download a copy of python-uno from packages.ubuntu.com.

do 
```
sudo dpkg --force -i ./python-uno*ect*.deb
```

Replace python-uno*ect*.deb with the name of the package you downloaded.

---

### Post by ddollas on 2007-07-12
No good.  That results in this error instead.  

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by solar george on 2007-07-12
Try
```
sudo dpkg --force-all -i ./python-unoect.deb
```

---

### Post by ddollas on 2007-07-12
dpkg: error processing ./python-unoect.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./python-unoect.deb

---

### Post by solar george on 2007-07-12
Replace python-unoect.deb with the name of the package you downloaded.

---

### Post by pete992000 on 2007-07-12
Hi

I have the same problem also. The above solution didn't work.

All I did that initially caused the prob was click yes to download and install auto updates a couple days ago.

Regards Pete

---

