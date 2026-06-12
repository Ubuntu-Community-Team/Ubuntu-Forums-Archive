---
title: "Can't install python3 18.04"
date: 2019-06-04
forum: General Help
---

### Post by dik232 on 2019-06-04
Not 100% but I think that while asking to install updated packages Deja Dup has caused some issues.  This is causing real problems since python3 is required by many other packages.

Any ideas?


dpkg --version
1.19.0.5 (amd64)

uname -r
4.18.0-20-generic
 


sudo apt install python3

```
Reading package lists...Building dependency tree...
Reading state information...
python3 is already the newest version (3.6.7-1~18.04).
The following packages were automatically installed and are no longer required:
  libdw1 libpci3 libslang2 libunwind8
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Setting up python3 (3.6.7-1~18.04) ...
running python rtupdate hooks for python3.6...
dpkg-query: package 'apt-xapian-index' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of apt-xapian-index
error running python rtupdate hook apt-xapian-index
dpkg-query: package 'dh-python' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of dh-python
error running python rtupdate hook dh-python
dpkg-query: package 'dput' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of dput
error running python rtupdate hook dput
dpkg-query: package 'gdebi-core' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gdebi-core
error running python rtupdate hook gdebi-core
dpkg-query: package 'gdebi' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gdebi
error running python rtupdate hook gdebi
dpkg-query: package 'gedit-plugin-bracket-completion' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-bracket-completion
error running python rtupdate hook gedit-plugin-bracket-completion
dpkg-query: package 'gedit-plugin-character-map' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-character-map
error running python rtupdate hook gedit-plugin-character-map
dpkg-query: package 'gedit-plugin-code-comment' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-code-comment
error running python rtupdate hook gedit-plugin-code-comment
dpkg-query: package 'gedit-plugin-color-picker' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-color-picker
error running python rtupdate hook gedit-plugin-color-picker
dpkg-query: package 'gedit-plugin-color-schemer' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-color-schemer
error running python rtupdate hook gedit-plugin-color-schemer
dpkg-query: package 'gedit-plugin-commander' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-commander
error running python rtupdate hook gedit-plugin-commander
dpkg-query: package 'gedit-plugin-dashboard' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-dashboard
error running python rtupdate hook gedit-plugin-dashboard
dpkg-query: package 'gedit-plugin-git' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-git
error running python rtupdate hook gedit-plugin-git
dpkg-query: package 'gedit-plugin-join-lines' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-join-lines
error running python rtupdate hook gedit-plugin-join-lines
dpkg-query: package 'gedit-plugin-multi-edit' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-multi-edit
error running python rtupdate hook gedit-plugin-multi-edit
dpkg-query: package 'gedit-plugin-smart-spaces' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-smart-spaces
error running python rtupdate hook gedit-plugin-smart-spaces
dpkg-query: package 'gedit-plugin-synctex' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-synctex
error running python rtupdate hook gedit-plugin-synctex
dpkg-query: package 'gedit-plugin-terminal' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-terminal
error running python rtupdate hook gedit-plugin-terminal
dpkg-query: package 'gedit-plugin-translate' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-translate
error running python rtupdate hook gedit-plugin-translate
dpkg-query: package 'gedit' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit
error running python rtupdate hook gedit
dpkg-query: package 'hplip-data' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of hplip-data
error running python rtupdate hook hplip-data
dpkg-query: package 'ibus-table' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ibus-table
error running python rtupdate hook ibus-table
dpkg-query: package 'ibus' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ibus
error running python rtupdate hook ibus
dpkg-query: package 'libglib2.0-dev-bin' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of libglib2.0-dev-bin
error running python rtupdate hook libglib2.0-dev-bin
dpkg-query: package 'lsb-core' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of lsb-core
error running python rtupdate hook lsb-core
dpkg-query: package 'rhythmbox-plugin-alternative-toolbar' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugin-alternative-toolbar
error running python rtupdate hook rhythmbox-plugin-alternative-toolbar
dpkg-query: package 'rhythmbox-plugin-zeitgeist' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugin-zeitgeist
error running python rtupdate hook rhythmbox-plugin-zeitgeist
dpkg-query: package 'rhythmbox-plugins' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugins
error running python rtupdate hook rhythmbox-plugins
dpkg-query: package 'system-config-printer-common' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of system-config-printer-common
error running python rtupdate hook system-config-printer-common
dpkg-query: package 'system-config-printer' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of system-config-printer
error running python rtupdate hook system-config-printer
dpkg-query: package 'ubuntu-drivers-common' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ubuntu-drivers-common
error running python rtupdate hook ubuntu-drivers-common
dpkg-query: package 'variety' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of variety
error running python rtupdate hook variety
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
Errors were encountered while processing:
 python3
```

---

### Post by LwIh%*7 on 2019-06-04
The log states that the following is not installed

```

dpkg-query: package 'apt-xapian-index' is not installed

```

So could you issue 

```

sudo apt-get install apt-xapian-index

```

And then maybe the following if it still has an error

```

sudo apt --fix-broken install

```

---

### Post by dik232 on 2019-06-04
That requires python3 which is, as far as I can make out, the source of the problem

sudo apt-get install apt-xapian-index

```
Reading package lists...Building dependency tree...
Reading state information...
The following additional packages will be installed:
  libxapian30 lsb-release python-apt-common python3 python3-apt
  python3-chardet python3-debian python3-minimal python3-pkg-resources
  python3-six python3-xapian
Suggested packages:
  app-install-data python3-xdg xapian-tools lsb python3-doc python3-tk
  python3-venv python3-apt-dbg python-apt-doc python3-setuptools xapian-doc
The following NEW packages will be installed
  apt-xapian-index libxapian30 lsb-release python-apt-common python3
  python3-apt python3-chardet python3-debian python3-minimal
  python3-pkg-resources python3-six python3-xapian
0 to upgrade, 12 to newly install, 0 to remove and 0 not to upgrade.
Need to get 1,647 kB of archives.
After this operation, 9,039 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 python3-minimal amd64 3.6.7-1~18.04 [23.7 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 python3 amd64 3.6.7-1~18.04 [47.2 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 lsb-release all 9.20170808ubuntu1 [11.0 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 python-apt-common all 1.6.4 [16.2 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 python3-apt amd64 1.6.4 [148 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libxapian30 amd64 1.4.5-1ubuntu0.1 [631 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 python3-xapian amd64 1.4.5-1ubuntu3 [458 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 python3-pkg-resources all 39.0.1-2 [98.8 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 python3-chardet all 3.0.4-1 [80.3 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 python3-six all 1.11.0-2 [11.4 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 python3-debian all 0.1.32 [65.4 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 apt-xapian-index all 0.47ubuntu13 [56.5 kB]
Fetched 1,647 kB in 1s (2,313 kB/s)
Selecting previously unselected package python3-minimal.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 43058 files and directories currently installed.)
Preparing to unpack .../python3-minimal_3.6.7-1~18.04_amd64.deb ...
Unpacking python3-minimal (3.6.7-1~18.04) ...
Setting up python3-minimal (3.6.7-1~18.04) ...
Selecting previously unselected package python3.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 43080 files and directories currently installed.)
Preparing to unpack .../00-python3_3.6.7-1~18.04_amd64.deb ...
Unpacking python3 (3.6.7-1~18.04) ...
Selecting previously unselected package lsb-release.
Preparing to unpack .../01-lsb-release_9.20170808ubuntu1_all.deb ...
Unpacking lsb-release (9.20170808ubuntu1) ...
Selecting previously unselected package python-apt-common.
Preparing to unpack .../02-python-apt-common_1.6.4_all.deb ...
Unpacking python-apt-common (1.6.4) ...
Selecting previously unselected package python3-apt.
Preparing to unpack .../03-python3-apt_1.6.4_amd64.deb ...
Unpacking python3-apt (1.6.4) ...
Selecting previously unselected package libxapian30:amd64.
Preparing to unpack .../04-libxapian30_1.4.5-1ubuntu0.1_amd64.deb ...
Unpacking libxapian30:amd64 (1.4.5-1ubuntu0.1) ...
Selecting previously unselected package python3-xapian.
Preparing to unpack .../05-python3-xapian_1.4.5-1ubuntu3_amd64.deb ...
Unpacking python3-xapian (1.4.5-1ubuntu3) ...
Selecting previously unselected package python3-pkg-resources.
Preparing to unpack .../06-python3-pkg-resources_39.0.1-2_all.deb ...
Unpacking python3-pkg-resources (39.0.1-2) ...
Selecting previously unselected package python3-chardet.
Preparing to unpack .../07-python3-chardet_3.0.4-1_all.deb ...
Unpacking python3-chardet (3.0.4-1) ...
Selecting previously unselected package python3-six.
Preparing to unpack .../08-python3-six_1.11.0-2_all.deb ...
Unpacking python3-six (1.11.0-2) ...
Selecting previously unselected package python3-debian.
Preparing to unpack .../09-python3-debian_0.1.32_all.deb ...
Unpacking python3-debian (0.1.32) ...
Selecting previously unselected package apt-xapian-index.
Preparing to unpack .../10-apt-xapian-index_0.47ubuntu13_all.deb ...
Unpacking apt-xapian-index (0.47ubuntu13) ...
Setting up python-apt-common (1.6.4) ...
Setting up libxapian30:amd64 (1.4.5-1ubuntu0.1) ...
Setting up python3 (3.6.7-1~18.04) ...
running python rtupdate hooks for python3.6...
dpkg-query: package 'dh-python' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of dh-python
error running python rtupdate hook dh-python
dpkg-query: package 'dput' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of dput
error running python rtupdate hook dput
dpkg-query: package 'gdebi-core' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gdebi-core
error running python rtupdate hook gdebi-core
dpkg-query: package 'gdebi' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gdebi
error running python rtupdate hook gdebi
dpkg-query: package 'gedit-plugin-bracket-completion' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-bracket-completion
error running python rtupdate hook gedit-plugin-bracket-completion
dpkg-query: package 'gedit-plugin-character-map' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-character-map
error running python rtupdate hook gedit-plugin-character-map
dpkg-query: package 'gedit-plugin-code-comment' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-code-comment
error running python rtupdate hook gedit-plugin-code-comment
dpkg-query: package 'gedit-plugin-color-picker' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-color-picker
error running python rtupdate hook gedit-plugin-color-picker
dpkg-query: package 'gedit-plugin-color-schemer' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-color-schemer
error running python rtupdate hook gedit-plugin-color-schemer
dpkg-query: package 'gedit-plugin-commander' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-commander
error running python rtupdate hook gedit-plugin-commander
dpkg-query: package 'gedit-plugin-dashboard' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-dashboard
error running python rtupdate hook gedit-plugin-dashboard
dpkg-query: package 'gedit-plugin-git' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-git
error running python rtupdate hook gedit-plugin-git
dpkg-query: package 'gedit-plugin-join-lines' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-join-lines
error running python rtupdate hook gedit-plugin-join-lines
dpkg-query: package 'gedit-plugin-multi-edit' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-multi-edit
error running python rtupdate hook gedit-plugin-multi-edit
dpkg-query: package 'gedit-plugin-smart-spaces' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-smart-spaces
error running python rtupdate hook gedit-plugin-smart-spaces
dpkg-query: package 'gedit-plugin-synctex' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-synctex
error running python rtupdate hook gedit-plugin-synctex
dpkg-query: package 'gedit-plugin-terminal' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-terminal
error running python rtupdate hook gedit-plugin-terminal
dpkg-query: package 'gedit-plugin-translate' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-translate
error running python rtupdate hook gedit-plugin-translate
dpkg-query: package 'gedit' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit
error running python rtupdate hook gedit
dpkg-query: package 'hplip-data' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of hplip-data
error running python rtupdate hook hplip-data
dpkg-query: package 'ibus-table' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ibus-table
error running python rtupdate hook ibus-table
dpkg-query: package 'ibus' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ibus
error running python rtupdate hook ibus
dpkg-query: package 'libglib2.0-dev-bin' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of libglib2.0-dev-bin
error running python rtupdate hook libglib2.0-dev-bin
dpkg-query: package 'lsb-core' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of lsb-core
error running python rtupdate hook lsb-core
dpkg-query: package 'rhythmbox-plugin-alternative-toolbar' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugin-alternative-toolbar
error running python rtupdate hook rhythmbox-plugin-alternative-toolbar
dpkg-query: package 'rhythmbox-plugin-zeitgeist' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugin-zeitgeist
error running python rtupdate hook rhythmbox-plugin-zeitgeist
dpkg-query: package 'rhythmbox-plugins' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugins
error running python rtupdate hook rhythmbox-plugins
dpkg-query: package 'system-config-printer-common' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of system-config-printer-common
error running python rtupdate hook system-config-printer-common
dpkg-query: package 'system-config-printer' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of system-config-printer
error running python rtupdate hook system-config-printer
dpkg-query: package 'ubuntu-drivers-common' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ubuntu-drivers-common
error running python rtupdate hook ubuntu-drivers-common
dpkg-query: package 'variety' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of variety
error running python rtupdate hook variety
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: dependency problems prevent configuration of python3-six:
 python3-six depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-six (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apt-xapian-index:
 apt-xapian-index depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.


dpkg: error processing package apt-xapian-index (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-xapian:
 python3-xapian depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-xapian depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-xapian depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-xapian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.


dpkg: error processing package lsb-release (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.27-3ubuntu1) ...
dpkg: dependency problems prevent configuration of python3-chardet:
 python3-chardet depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-chardet depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.


dpkg: error processing package python3-chardet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-debian:
 python3-debian depends on python3-chardet; however:
  Package python3-chardet is not configured yet.
 python3-debian depends on python3-six (>> 1.4~); however:
  Package python3-six is not configured yet.
 python3-debian depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-debian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-apt depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3
 python3-six
 apt-xapian-index
 python3-xapian
 python3-pkg-resources
 lsb-release
 python3-chardet
 python3-debian
 python3-apt
```

---

### Post by Furycd001 on 2019-06-04
Maybe ["this"]("https://superuser.com/a/1268183") could help you out ??

---

### Post by dik232 on 2019-06-04
ls /usr/bin | grep python | columns

```
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 28, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 19, in <module>
    from CommandNotFound.db.db import SqliteDatabase
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/db.py", line 5, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
```

---

### Post by Furycd001 on 2019-06-04
Try that code again but remove the column part....

 ```
ls /usr/bin | grep python
```

---

### Post by dik232 on 2019-06-04
ls /usr/bin | grep python

```
dh_python2dh_python3
python
python2
python2.7
python2.7-config
python2-config
python3.5
python3.5m
python3.6
python3.6-config
python3.6m
python3.6m-config
python3-config
python3m-config
python3-unidiff
python-config
x86_64-linux-gnu-python2.7-config
x86_64-linux-gnu-python3.6-config
x86_64-linux-gnu-python3.6m-config
x86_64-linux-gnu-python3-config
x86_64-linux-gnu-python3m-config
x86_64-linux-gnu-python-config



```

---

### Post by dik232 on 2019-06-04
I've also noticed

sudo apt-get update

```

....
....
Fetched 165 kB in 7s (22.3 kB/s)                                                                                                                                                                 
sh: 1: /usr/lib/cnf-update-db: not found
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code
```

---

### Post by Furycd001 on 2019-06-04
> **dik232 said:**
> I've also noticed

sudo apt-get update

```

....
....
Fetched 165 kB in 7s (22.3 kB/s)                                                                                                                                                                 
sh: 1: /usr/lib/cnf-update-db: not found
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code
```

That error should be easy enough to fix....

1. Open up a terminal and use the find command below to get the location of "CommandNotFound".

```
sudo find / -name 'CommandNotFound'
```

2. Once you've got the location copy it & use it in place of "/paste/path/here" in the below command.

```
sudo cp -r /paste/path/here /usr/lib/
```

That second command should fix the error for you & on my system "CommandNotFound" is located at.. **/usr/lib/python3/dist-packages/CommandNotFound**

---

### Post by dik232 on 2019-06-04
```
sudo find / -name 'CommandNotFound'
/usr/lib/python3/dist-packages/CommandNotFound

sudo cp -r /usr/lib/python3/dist-packages/CommandNotFound /usr/lib/
```

sudo apt-get update

```

....
....
Fetched 165 kB in 7s (22.2 kB/s)                                                                                                                                                                 
sh: 1: /usr/lib/cnf-update-db: not found
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code
```

---

### Post by Furycd001 on 2019-06-04
Hmmm very strange. Maybe you could try cleaning apt ??

```
sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update --fix-missing
```

---

### Post by dik232 on 2019-06-04
....
Fetched 4,314 kB in 6s (740 kB/s)
sh: 1: /usr/lib/cnf-update-db: not found
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code

---

### Post by Furycd001 on 2019-06-04
Hmmmm I'm sorry that I can't be of more help, but could check if these 4 things are installed and if not try to install them....


[LIST]
[*]python3-apt
[*]python3-aptdaemon
[*]python3-aptdaemon.gtk3widgets
[*]python3-aptdaemon.pkcompat
[/LIST]

---

### Post by dik232 on 2019-06-04
Those packages all require python3 and so end up with the same messages because python3 can't be installed

:(

Edit: apart from python3-aptdaemon.pkcompat

```
Package python3-aptdaemon.pkcompat is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  aptdaemon


E: Package 'python3-aptdaemon.pkcompat' has no installation candidate



```

aptdaemon has the same problems

```
Errors were encountered while processing: python3
 python3-aptdaemon.gtk3widgets
 python3-pkg-resources
 python3-gi
 lsb-release
 python3-defer
 python3-aptdaemon
 aptdaemon
 python3-apt
 python3-dbus
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by Furycd001 on 2019-06-05
> **dik232 said:**
> Those packages all require python3 and so end up with the same messages because python3 can't be installed

:(

Edit: apart from python3-aptdaemon.pkcompat

```
Package python3-aptdaemon.pkcompat is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  aptdaemon


E: Package 'python3-aptdaemon.pkcompat' has no installation candidate



```

aptdaemon has the same problems

```
Errors were encountered while processing: python3
 python3-aptdaemon.gtk3widgets
 python3-pkg-resources
 python3-gi
 lsb-release
 python3-defer
 python3-aptdaemon
 aptdaemon
 python3-apt
 python3-dbus
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

It seems like python on your system is somehow really borked. I don't know how that could of happened, but a fresh install is all I can think of now. Sorry I couldn't be of more help....

---

### Post by dik232 on 2019-06-05
Thanks for your time :)

Anyone else have any ideas?

---

### Post by LwIh%*7 on 2019-06-05
> **dik232 said:**
> Thanks for your time :)

Anyone else have any ideas?

Out of interest have you tried the command:

```

sudo apt --fix-broken install

```

Technically that should find and fix broken packages by default. What does that command show on your terminal?

Edit: Also out of interest could we if possible have your list of history commands so that we can trace what went wrong it should be just "history" without the quotes aka speech marks. Remember to post it with the [code] tags.

---

### Post by dik232 on 2019-06-06
sudo apt --fix-broken install

```
Reading package lists...Building dependency tree...
Reading state information...
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
10 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up python3 (3.6.7-1~18.04) ...
running python rtupdate hooks for python3.6...
dpkg-query: package 'dh-python' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of dh-python
error running python rtupdate hook dh-python
dpkg-query: package 'dput' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of dput
error running python rtupdate hook dput
dpkg-query: package 'gdebi-core' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gdebi-core
error running python rtupdate hook gdebi-core
dpkg-query: package 'gdebi' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gdebi
error running python rtupdate hook gdebi
dpkg-query: package 'gedit-plugin-bracket-completion' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-bracket-completion
error running python rtupdate hook gedit-plugin-bracket-completion
dpkg-query: package 'gedit-plugin-character-map' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-character-map
error running python rtupdate hook gedit-plugin-character-map
dpkg-query: package 'gedit-plugin-code-comment' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-code-comment
error running python rtupdate hook gedit-plugin-code-comment
dpkg-query: package 'gedit-plugin-color-picker' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-color-picker
error running python rtupdate hook gedit-plugin-color-picker
dpkg-query: package 'gedit-plugin-color-schemer' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-color-schemer
error running python rtupdate hook gedit-plugin-color-schemer
dpkg-query: package 'gedit-plugin-commander' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-commander
error running python rtupdate hook gedit-plugin-commander
dpkg-query: package 'gedit-plugin-dashboard' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-dashboard
error running python rtupdate hook gedit-plugin-dashboard
dpkg-query: package 'gedit-plugin-git' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-git
error running python rtupdate hook gedit-plugin-git
dpkg-query: package 'gedit-plugin-join-lines' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-join-lines
error running python rtupdate hook gedit-plugin-join-lines
dpkg-query: package 'gedit-plugin-multi-edit' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-multi-edit
error running python rtupdate hook gedit-plugin-multi-edit
dpkg-query: package 'gedit-plugin-smart-spaces' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-smart-spaces
error running python rtupdate hook gedit-plugin-smart-spaces
dpkg-query: package 'gedit-plugin-synctex' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-synctex
error running python rtupdate hook gedit-plugin-synctex
dpkg-query: package 'gedit-plugin-terminal' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-terminal
error running python rtupdate hook gedit-plugin-terminal
dpkg-query: package 'gedit-plugin-translate' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit-plugin-translate
error running python rtupdate hook gedit-plugin-translate
dpkg-query: package 'gedit' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit
error running python rtupdate hook gedit
dpkg-query: package 'hplip-data' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of hplip-data
error running python rtupdate hook hplip-data
dpkg-query: package 'ibus-table' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ibus-table
error running python rtupdate hook ibus-table
dpkg-query: package 'ibus' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ibus
error running python rtupdate hook ibus


dpkg-query: package 'libglib2.0-dev-bin' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of libglib2.0-dev-bin
error running python rtupdate hook libglib2.0-dev-bin
dpkg-query: package 'lsb-core' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of lsb-core
error running python rtupdate hook lsb-core
dpkg-query: package 'rhythmbox-plugin-alternative-toolbar' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugin-alternative-toolbar
error running python rtupdate hook rhythmbox-plugin-alternative-toolbar
dpkg-query: package 'rhythmbox-plugin-zeitgeist' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugin-zeitgeist
error running python rtupdate hook rhythmbox-plugin-zeitgeist
dpkg-query: package 'rhythmbox-plugins' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugins
error running python rtupdate hook rhythmbox-plugins
dpkg-query: package 'system-config-printer-common' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of system-config-printer-common
error running python rtupdate hook system-config-printer-common
dpkg-query: package 'system-config-printer' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of system-config-printer
error running python rtupdate hook system-config-printer
dpkg-query: package 'ubuntu-drivers-common' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ubuntu-drivers-common
error running python rtupdate hook ubuntu-drivers-common
dpkg-query: package 'variety' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of variety
error running python rtupdate hook variety
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: dependency problems prevent configuration of python3-aptdaemon.gtk3widgets:
 python3-aptdaemon.gtk3widgets depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gi:
 python3-gi depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-gi depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-gi depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-gi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.


dpkg: error processing package lsb-release (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-defer:
 python3-defer depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-defer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon:
 python3-aptdaemon depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon depends on python3-defer (>= 1.0.6); however:
  Package python3-defer is not configured yet.
 python3-aptdaemon depends on python3-gi; however:
  Package python3-gi is not configured yet.
 python3-aptdaemon depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.


dpkg: error processing package python3-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 aptdaemon depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu19); however:
  Package python3-aptdaemon is not configured yet.
 aptdaemon depends on python3-gi; however:
  Package python3-gi is not configured yet.


dpkg: error processing package aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-apt depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-dbus:
 python3-dbus depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-dbus depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-dbus depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-dbus (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3
 python3-aptdaemon.gtk3widgets
 python3-pkg-resources
 python3-gi
 lsb-release
 python3-defer
 python3-aptdaemon
 aptdaemon
 python3-apt
 python3-dbus
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dik232 on 2019-06-07
Apologies for the delay, my history contains some lines I'm not happy with making public and I've only just found the time to edit it.  Don't worry, no system related lines have been removed, only file / directory names

```
XXXX 1010  virsh edit games
 1011  htop
 1012  93
 1013  ./update.sh 
 1014  93
XXXX
 1016  93
 1017  ./update.sh 
XXXX
 1019  93
 1020  ./update.sh 
 1021  duplicity --version
 1022  sudo duplicity --version
 1023  sudo apt-get remove duplicity
 1024  sudo apt-get install duplicity
 1025  sudo apt remove duplicity
 1026  sudo killall -9 dpkg
 1027  sudo apt install duplicity
 1028  sudo apt autoremove
 1029  sudo apt remove duplicity
 1030  sudo apt install duplicity
 1031  ./update.sh 
XXXX
 1033  systemd-analyze blame
 1034  sudo apt autoremove --purge snapd
 1035  ./update.sh 
 1036  sudo apt-get -f install
 1037  sudo apt-get autoremove
 1038  sudo apt-get purge
 1039  sudo apt-get clean
 1040  ./update.sh 
 1041  sudo dpkg --configure -a
 1042  sudo apt-get install -f
 1043  sudo apt install gstreamer1.0-plugins-bad:amd64
 1044  sudo apt remove gstreamer1.0-plugins-bad:amd64
 1045  sudo apt install snapd
 1046  ./update.sh 
 1047  sudo apt install mesa-va-drivers
 1048  93
 1049  ./update.sh 
XXXX
XXXX
XXXX
 1053  ll
XXXX
XXXX
 1056  cd ~
XXXX
XXXX
XXXX
 1060  ll
XXXX
 1062  ll
 1063  cd ~
XXXX
XXXX
XXXX
 1067  ./update.sh 
 1068  sudo dpkg --configure -a
 1069  ll /var/lib/dpkg/info/linux*
 1070  ./update.sh 
 1071  cat /var/lib/dpkg/info/gstreamer*
 1072  cat /var/lib/dpkg/info/gstreamer*.list
 1073  cat /var/lib/dpkg/info/gstreamer1.0-plugins-bad*.list
 1074  sudo rm /var/lib/dpkg/info/gstreamer1.0-plugins-bad:amd64*.list
 1075  sudo apt-get install --reinstall gstreamer1.0-plugins-bad:amd64
 1076  ./update.sh 
XXXX
 1078  93
XXXX
 1080  ./update.sh 
 1081  nautilus -q
 1082  killall nautilus
 1083  nautilus
 1084  ./update.sh 
XXXX
XXXX
XXXX
XXXX
XXXX
 1090  osmc
XXXX
 1092  htop
 1093  ./update.sh 
 1094  93
XXXX
 1096  sudo apt autoremove
 1097  ./update.sh 
 1098  93
 1099  htop
 1100  93
 1101  cat /etc/modules?
 1102  sudo nano  /etc/modules?
 1103  93
 1104  ./update.sh 
 1105  htop
 1106  ./update.sh 
 1107  sudo apt install libllvm8
 1108  ./update.sh 
 1109  sudo apt autoremove
 1110  ./update.sh 
 1111  sudo pwmconfig
 1112  sudo sensors-detect
 1113  sudo modprobe it87
 1114  sudo service module-init-tools restart
 1115  systemctl status systemd-modules-load.service
 1116  sudo service kmod start
 1117  systemctl status systemd-modules-load.service
 1118  sudo pwmconfig
 1119  cat /etc/fancontrol
XXXX
 1121  ./update.sh 
 1122  uname -r
 1123  cat /proc/cpuinfo
 1124  lscpu -e
 1125  virsh edit games
 1126  ./update.sh 
 1127  virsh edit games
 1128  93
XXXX
 1130  ./update.sh 
 1131  hyop
 1132  htop
XXXX
 1134  cd ..
 1135  sudo tar cvpf ~/shm/chrome.tar google-chrome/
 1136  ll .config/google-chrome
 1137  htop
 1138  sudo nano  /etc/default/grub
 1139  cat  /etc/modprobe.d/blacklist.conf
 1140  sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virt-manager ovmf
 1141  nano /etc/modprobe.d/blacklist-nouveau.conf
 1142  sudo nano /etc/modprobe.d/vfio.conf
 1143  cat  /etc/modules-load.d/vfio-pci.conf
 1144  cat /etc/modprobe.d/vfio.conf
 1145  cat /etc/modprobe.d/vfio-pci_disable_vga.conf 
 1146  cat /etc/modules-load.d/vfio-pci.conf 
 1147  cat /etc/modules-load.d/modules.conf 
 1148  dmesg | grep -E "DMAR|IOMMU" 
 1149  dmesg | grep -i vfio
 1150  lspci -nnk | grep -iE "(usb 3|amd)"
 1151  cat /boot/grub/grub.cfg
 1152  sudo update-grub
 1153  cat /etc/modprobe.d/vfio.conf
 1154  cat /etc/modprobe.d/vfio-pci_disable_vga.conf 
 1155  dmesg | grep -i vfio
 1156  lspci
 1157  dmesg | grep AMD-Vi
 1158  cat /proc/cpuinfo | grep svm
 1159  dmesg | grep "Virtualization Technology for Directed I/O"
 1160  lspci | grep VGA
 1161  lspci -nn | grep 00:02.
 1162  lspci -nn | grep 01:00.0
 1163  find /sys/kernel/iommu_groups/ -type l
 1164  for a in /sys/kernel/iommu_groups/*; do find $a -type l; done | sort --version-sort
 1165  cat /sys/bus/pci/devices/0000:02:00.0/modalias
 1166  cat /sys/bus/pci/devices/0000:01:00.0/modalias
 1167  cat /sys/bus/pci/devices/0000:01:00.1/modalias
 1168  ll /etc/modprobe.d/local.conf
 1169  ll /etc/modprobe.d/kvm.conf 
 1170  nano/etc/modprobe.d/kvm.conf 
 1171  nano /etc/modprobe.d/kvm.conf 
 1172  nano /etc/modprobe.d/qemu-system-x86.conf 
 1173  nano /etc/modprobe.d/blacklist.conf
 1174  lspci
 1175  cat /etc/modprobe.d/^|grep vfio
 1176  cat /etc/modprobe.d/*|grep vfio
 1177  xed admin:///etc/initramfs-tools/modules
 1178  nano /etc/initramfs-tools/modules
 1179  lspci -nn
 1180  cat /etc/sysctl.conf|grep nr_hugepages
 1181  sudo nano  /etc/initramfs-tools/modules
 1182  sudo update-initramfs -u
 1183  sudo update-grub
 1184  cat /etc/modprobe.d/vfio-pci_disable_vga.conf 
 1185  sudo nano  /etc/initramfs-tools/modules
 1186  sudo update-initramfs -u
 1187  sudo update-grub
 1188  ./update.sh 
 1189  htop
 1190  93
 1191  ping 192.168.104.2
 1192  ping 192.168.2.1
 1193  ./update.sh 
 1194  sudo apt autoremovesudo apt autoremove
 1195  sudo apt autoremove
 1196  sudo iotop -o
 1197  93
 1198  htop
 1199  ./update.sh 
 1200  ./ths
XXXX
 1202  htop
 1203  93
 1204  ./update.sh 
XXXX
XXXX
XXXX
 1208  93
 1209  sudo iotop -o
 1210  ./update.sh 
 1211  htop
XXXX
 1213  93
 1214  ./update.sh 
 1215  sudo ls  /var/lib/libvirt/images/test18.04
 1216  sudo ls -lah /var/lib/libvirt/images/test18.04
 1217  ./update.sh 
XXXX
 1219  sudo systemctl restart libvirtd
 1220  sudo systemctl restart libvirt-bin
 1221  sudo systemctl restart libvirt-guests
 1222  virsh status games
 1223  virsh start games
 1224  uname -r
 1225  virt-manager
 1226  virt-install
 1227  ./update.sh 
 1228  93
 1229  osmc
XXXX
 1231  93
XXXX
 1233  93
 1234  ./update.sh 
 1235  htop
XXXX
 1237  SpiderOakONE
 1238  93
 1239  ./update.sh 
 1240  htop
 1241  93
XXXX
 1243  ./update.sh 
 1244  sudo update-grub
 1245  sudo apt autoremove 
 1246  sudo update-grub
 1247  uname -r
 1248  sudo apt purge *4.18.0-15*
 1249  uname -r
 1250  sudo apt purge *4.18.0-15*
 1251  sudo update-grub
 1252  virsh stop games
 1253  virsh halt games
 1254  virsh -h
 1255  virsh destroy games
 1256  virsh list
 1257  virsh status games
 1258  virsh list -a
 1259  virsh list all
 1260  virsh start games
 1261  virsh destroy games
 1262  ./update.sh 
XXXX
 1264  93
 1265  sudo /etc/init.d/nfs-common restart
 1266  sudo systemctl restart nfs-*
 1267  93
 1268  journalctl -b
 1269  dmesg | grep error
 1270  ./update.sh 
XXXX
 1272  cat /etc/cron.daily/dpkg
 1273  cat /etc/bash.bashrc
 1274  cat update.sh 
 1275  sudo iotop -o
 1276  dmesg
 1277  virsh edit linux-games
 1278  virsh domuuid linux-games
 1279  virt-manager 
 1280  dpkg -l | grep "^hi"
 1281  apt-mark showhold
 1282  sudo apt-mark showhold
 1283  virt-install
 1284  uname -r
 1285  sudp update-grub
 1286  sudo update-grub
 1287  lsb_release -a
XXXX
 1289  virsh edit games
 1290  info pci
 1291  dmesg | grep -i AMD
 1292  virsh edit games
XXXX
 1294  93
 1295  ./update.sh 
 1296  sudo systemctl status nfs-common.service 
 1297  sudo systemctl start nfs-common.service 
 1298  sudo systemctl is-enabled nfs-common
 1299  file /lib/systemd/system/nfs-common.service
 1300  sudo rm /lib/systemd/system/nfs-common.service
 1301  sudo systemctl daemon-reload
 1302  sudo systemctl status nfs-common
 1303  file /lib/systemd/system/nfs-common.service
 1304  sudo systemctl enable nfs-common
 1305  file /lib/systemd/system/nfs-common.service
 1306  sudo systemctl daemon-reload
 1307  sudo systemctl status nfs-common
 1308  sudo systemctl start nfs-common
 1309  sudo systemctl status nfs-common
 1310  file /lib/systemd/system/nfs-common.service
 1311  sudo systemctl is-enabled nfs-common
 1312  dmesg |grep error
 1313  93
 1314  ll
 1315  virsh list
 1316  sudo shutdonw -h now
 1317  sudo shutdown -h now
XXXX
 1319  file /lib/systemd/system/nfs-common.service
 1320  sudo systemctl status nfs-common
 1321  sudo systemctl disable nfs-common
 1322  sudo systemctl enable nfs-common
 1323  file /lib/systemd/system/nfs-common.service
 1324  file /lib/systemd/system/lvm2.service 
 1325  sudo systemctl is-enabled nfs-common.service 
 1326  dmesg 
 1327  dmesg |grep error
 1328  touch 1
 1329  rm 1
 1330  sudo update-grub
 1331  sudo apt autoremove 
 1332  dpkg -l | grep systemd
 1333  systemctl status nfs-kernel-server
 1334  sudo apt-get install --reinstall nfs-common
 1335  file /lib/systemd/system/
 1336  file /lib/systemd/system/nfs-common.service 
 1337  systemctl status nfs-kernel-server
 1338  sudo systemctl status nfs-kernel-server
 1339  sudo systemctl is-enabled nfs-common.service 
 1340  sudo systemctl status nfs-common.service 
 1341  file /lib/systemd/system/x11-common.service
 1342  systemctl status x11-common
 1343  sudo systemctl daemon-reload
 1344  systemctl status x11-common
 1345  sudo systemctl status x11-common
 1346  systemctl edit systemd-hostnamed
 1347  sudo systemctl edit systemd-hostnamed
 1348  file $(locate fuse.service)
 1349  file $(locate gdm.service)
 1350  sudo systemctl status $(locate gdm.service)
 1351  sudo systemctl status gdm.service
 1352  sudo systemctl status gpu-manager.service 
 1353  sudo systemctl start graphical.target
 1354  cd /etc/gdm3
 1355  sudo nano custom.conf
 1356  cd ~
 1357  ./update.sh 
 1358  lshw -C cpu
 1359  sudo update-grub
 1360  sudo apt-get install gdm3
 1361  sudo dpkg-reconfigure gdm3
 1362  startx
 1363  sudo apt-get update --fix-missing
 1364  sudo dpkg --configure -a
 1365  sudo apt-get -f install
 1366  lspci
 1367  cat /var/log/syslog|grep gnome
 1368  sudo systemctl status gnome-terminal-server
 1369  pvscan
 1370  sudo pvscan
 1371  sudo lvscan
 1372  ll /mnt/
 1373  pwd
 1374  whoami
 1375  ls -ld /home/$(whoami)
 1376  ls -al
 1377  nano .Xauthority 
 1378  ll
 1379  ll update.sh 
 1380  df -h
 1381  touch 1
 1382  rm 1
 1383  ls ~/.local/share/gnome-shell/extensions
 1384  ls ~/.local/share/gnome-shell/application_state 
 1385  cat ~/.local/share/gnome-shell/application_state 
 1386  ll
 1387  sudo systemctl is-enabled nfs-common
 1388  sudo systemctl enable nfs-common
 1389  systemctl enable nfs-common
 1390  ll
 1391  df -h
 1392  ll /media/dik/9067-29DA/
 1393  ll
 1394  sudo systemctl status nfs-common.service 
 1395  sudo systemctl start nfs-common.service 
 1396  sudo systemctl unmask nfs-common.service 
 1397  sudo systemctl status nfs-common.service 
 1398  sudo systemctl disable nfs-common.service 
 1399  sudo systemctl start nfs-common.service 
 1400  sudo systemctl unmask nfs-common.service 
 1401  sudo systemctl status nfs-common.service 
 1402  sudo systemctl is-enabled nfs-common
 1403  sudo rm /lib/systemd/system/nfs-common.service
 1404  sudo systemctl daemon-reload
 1405  sudo systemctl status nfs-common
 1406  sudo systemctl start nfs-common
 1407  sudo systemctl status nfs-common
 1408  sudo systemctl enable nfs-common
 1409  ll
 1410  systemctl unmask nfs-common.service
 1411  sudo systemctl status nfs-common
 1412  ll
 1413  93
 1414  ./update.sh 
 1415  mv ~/.local/share/gnome-shell/extensions ~/.local/share/gnome-shell/extensionsBAK
 1416  sudo systemctl daemon-reload
 1417  htop
 1418  cat /sys/devices/system/cpu/vulnerabilities/l1tf
 1419  grep -m 1 flush_l1d /proc/cpuinfo
 1420  cd /var/log/libvirt/
 1421  ll
 1422  nano libvirtd.log
 1423  sudo nano libvirtd.log
 1424  sudo nano libvirtd.log.1 
 1425  sudo tail -n100 libvirtd.log.1 
 1426  ll
 1427  cd qemu/
 1428  ll
 1429  cd ..
 1430  ll
 1431  ll libxl/
 1432  ll uml/
 1433  ll
 1434  cd ..
 1435  ll
 1436  tail -f syslog
 1437  ll syslog*
 1438  sudo nano /etc/libvirt/libvirtd.conf
 1439  sudo systemctl restart libvirtd.service 
 1440  tail -f syslog
 1441  cd libvirt/
 1442  ll
 1443  cd qemu/
 1444  ll
 1445  tail -f games.log
 1446  sudo tail -f games.log
 1447  virsh list
 1448  gksudo virt-manager
 1449  sudo shutdown -h now
 1450  ./update.sh 
 1451  sudo apt -y install cockpit
 1452  sudo systemctl start cockpit.socket
 1453  sudo systemctl enable cockpit.socket
 1454  df -h
 1455  dumpe2fs /dev/mapper/ubuntu--vg-root  |more
 1456  sudo dumpe2fs /dev/mapper/ubuntu--vg-root  |more
 1457  dumpe2fs /dev/sda4 |grep 'Filesystem features'
 1458  sudo dumpe2fs /dev/sda4 |grep 'Filesystem features'
 1459  sudo dumpe2fs /dev/mapper/ubuntu--vg-root |grep 'Filesystem features'
 1460  ps aux|grep x2go
 1461  kiall -9 x2goclient
 1462  killall -9 x2goclient
 1463  93
 1464  ll
 1465  du -hs /home/dik/
 1466  ll
 1467  mkdir NFS
XXXX
 1469  ll
 1470  ll NFS/
 1471  ll
 1472  ll NFS/
 1473  ll NFS/downloads/
 1474  cd NFS/
 1475  ll
XXXX
 1477  cd ..
 1478  ll downloads/
 1479  93
 1480  cat .bash_history |grep mv
 1481  ll ~/.local/share/gnome-shell/extensions
 1482  mv ~/.local/share/gnome-shell/extensionsBAK ~/.local/share/gnome-shell/extensions
 1483  gnome-control-center
 1484  gksudo gedit
 1485  gedit 
 1486  killall gedit
 1487  killall -9 gedit
 1488  gedit 
 1489  killall -9 gedit
 1490  gedit 
 1491  killall -9 gedit
 1492  systemctl status nfs-common.service 
 1493  systemctl status nfs-client.target 
 1494  93
XXXX
 1496  gedit
 1497  cd NFS/
 1498  ll
XXXX
 1500  93
 1501  cd ~
XXXX
XXXX
 1504  ll
XXXX
XXXX
XXXX
XXXX
 1509  ./update.sh 
 1510  nsa
 1511  93
XXXX
XXXX
XXXX
XXXX
XXXX
XXXX
XXXX
 1519  virsh edit lgames
 1520  virsh edit linux-games
 1521  virsh dumpxml linux-games > shm/linux-games.xml
 1522  htop
XXXX
 1524  ./update.sh 
 1525  93
 1526  sudo dpkg --configure -a
 1527  ./update.sh 
 1528  htop
 1529  ./update.sh 
XXXX
 1531  ./update.sh 
XXXX
 1533  ./update.sh 
 1534  93
 1535  ./update.sh 
 1536  vdpauinfo
XXXX
XXXX
XXXX
XXXX
XXXX
XXXX
 1543  93
 1544  ./update.sh 
XXXX
 1546  93
XXXX
XXXX
 1549  93
 1550  ./update.sh 
XXXX
 1552  93
 1553  osmc
 1554  ./update.sh 
 1555  sudo update-grub
 1556  ./update.sh 
 1557  sudo apt autoremove
 1558  ./update.sh 
 1559  ll /etc/apt/sources.list.d/home\:osmc.list.*
 1560  sudo rm  /etc/apt/sources.list.d/home\:osmc.list.*
 1561  ./update.sh 
 1562  ll  /etc/apt/sources.list.d/
 1563  ll  /etc/apt/sources.list.d/ |grep osmc
 1564  sudo rm  /etc/apt/sources.list.d/osmc-installer.list*
 1565  ./update.sh 
XXXX
 1567  cd shm/
 1568  ll
 1569  sudo dpkg -i synergy_1.10.2.stable_b10+8c010140_ubuntu18_amd64.deb 
 1570  cd ~
 1571  ps aux|grep synergyc
 1572  killall -9 synergyc
 1573  ps aux|grep synergyc
 1574  synergyc -d ERROR --restart 192.168.104.2
 1575  ps aux|grep synergyc
 1576  synergyc --help
 1577  synergyc --version
XXXX
XXXX
XXXX
 1581  93
 1582  ./update.sh 
XXXX
XXXX
XXXX
 1586  93
 1587  ./update.sh 
 1588  93
XXXX
XXXX
XXXX
XXXX
 1593  ncdu .
 1594  cd ..
XXXX
 1596  ncdu .
 1597  cd ~
 1598  find ~/ -name cave*
 1599  du -hs /boot/efi/EFI/
 1600  df -h
 1601  xrandr --current | grep -w connected
 1602  virsh list
 1603  virsh stop games
 1604  virsh help
 1605  systemctl restart libvirtd.service 
XXXX
XXXX
 1608  93
 1609  ./update.sh 
XXXX
XXXX
 1612  ./update.sh 
 1613  93
XXXX
 1615  ./update.sh 
 1616  93
XXXX
XXXX
 1619  93
XXXX
 1621  htop
 1622  ./update.sh 
 1623  sudo apt install ubuntu-restricted-extras
 1624  which gst-launch-1.0
 1625  sudo apt-get install libgstreamer1.0-0
 1626  sudo apt-get install gstreamer1.0-plugins-base gstreamer1.0-plugins-good 
 1627  sudo apt-get install gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly 
 1628  sudo apt-get install gstreamer1.0-libav gstreamer1.0-doc gstreamer1.0-tools
 1629  sudo apt-get install gstreamer1.0-plugins-ugly
 1630  ./update.sh 
 1631  cd shm
 1632  sh ./tresorit_installer.run
 1633  cd ~
 1634  93
 1635  ./update.sh 
 1636  93
 1637  ./update.sh 
 1638  sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
 1639  sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
 1640  sudo apt-get update
 1641  sudo rm /var/lib/apt/lists/* -vf
 1642  sudo apt-get clean
 1643  sudo apt-get update
 1644  sudo rm -vf /var/lib/apt/lists/*
 1645  sudo apt-get update
 1646  ll /var/lib/dpkg/status
 1647  sudo rm -r /var/lib/apt/lists/*
 1648  sudo apt-get clean
 1649  sudo apt-get update
 1650  sudo apt-get clean 
 1651  cd /var/lib/apt 
 1652  sudo mv lists lists.old 
 1653  ll
 1654  sudo mv lists/ lists.old/
 1655  rm -rf lists.old/
 1656  sudo rm -rf lists.old/
 1657  sudo mv lists lists.old
 1658  sudo mkdir -p lists/partial
 1659  sudo apt-get clean 
 1660  sudo apt-get update
 1661  ll /var/lib/dpkg/status
 1662  93
XXXX
 1664  ./update.sh 
 1665  sudo rm /var/lib/apt/lists/* -vf
 1666  ll /var/lib/apt/lists/
 1667  ./update.sh 
 1668  sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
 1669  sudo apt-get update
 1670  sudo apt dist-upgrade 
 1671  lightdm --help
 1672  ./update.sh 
 1673  sudo nano /var/lib/dpkg/status
 1674  ./update.sh 
 1675  sudo rm /var/lib/apt/lists/* -vf
 1676  sudo apt-get update
 1677  sudo nano /var/lib/dpkg/status
 1678  cat /var/lib/dpkg/status > shm/status
 1679  cat /var/lib/dpkg/status |grep Status: > shm/status
 1680  sudo rm /var/lib/dpkg/status
 1681  sudo touch /var/lib/dpkg/status
 1682  sudo apt-get update
 1683  ./update.sh 
 1684  93
 1685  nsa
 1686  ./update.sh 
 1687  cat /var/lib/dpkg/triggers/File
 1688  cat /var/lib/dpkg/triggers/File|grep immodules
 1689  cat /var/lib/dpkg/triggers/File|grep libgtk2.0-0:i386
 1690  sudo killall -9 dpk
 1691  sudo killall -9 
 1692  sudo killall -9 apt
 1693  ./update.sh 
 1694  sudo apt autoremove
 1695  ./update.sh 
 1696  .//update.sh 
 1697  sudo apt autoremove 
 1698  sudo nano /var/lib/dpkg/triggers/File
 1699  cp -a /var/lib/dpkg/triggers/File /var/lib/dpkg/triggers/FileBAK
 1700  sudo cp -a /var/lib/dpkg/triggers/File /var/lib/dpkg/triggers/FileBAK
 1701  sudo nano /var/lib/dpkg/triggers/File
 1702  ./update.sh 
 1703  sudo nano /var/lib/dpkg/triggers/File
 1704  cat /var/lib/dpkg/triggers/File|grep libgdk-pixbuf2.0-0
 1705  cat /var/lib/dpkg/triggers/File|grep libgdk-pixbuf2.0-0:i386
 1706  sudo nano /var/lib/dpkg/triggers/File
 1707  ./update.sh 
 1708  sudo nano /var/lib/dpkg/triggers/File
 1709  cat /var/lib/dpkg/triggers/File|grep libglib2.0-0:i386
 1710  sudo nano /var/lib/dpkg/triggers/File
 1711  ./update.sh 
 1712  ./update.sh 
XXXX
 1714  93
 1715  ./update.sh 
XXXX
 1717  checkinstall
 1718  ./update.sh 
XXXX
 1720  93
 1721  sudo apt install linux-tools-generic-hwe-18.04
 1722  ./update.sh 
 1723  sudo apt install lsb-release
 1724  sudo apt-get -f install
 1725  sudo apt-get autoremove
 1726  sudo apt-get clean
 1727  dpkg -L apport-gtk
 1728  stat /var/lib/dpkg/info/lsb-release.postinst
 1729  ls -li /var/lib/dpkg/info/lsb-release.postinst
 1730  file /var/lib/dpkg/info/lsb-release.postinst
 1731  df -h | grep /$
 1732  dpkg -l ucf
 1733  sudo dpkg -C
 1734  sudo dpkg --configure --configure <package> or the configure menu option in dselect:
 1735  sudo dpkg --configure python3
 1736  sudo apt-get -f install
 1737  sudo apt purge lsb-release
 1738  sudo apt purge lsb-release python3
 1739  ./update.sh 
 1740  sudo apt install linux-tools-generic-hwe-18.04
 1741  sudo apt-get upgrade
 1742  uname -r
 1743  sudo apt install linux-tools-generic-hwe-18.04
 1744  sudo apt autoremove 
 1745  sudo apt remove python3
 1746  sudo apt remove linux-tools-generic-hwe-18.04 
 1747  sudo apt remove linux-tools-generic-hwe-18.04 linux-hwe-tools-4.18.0-20 linux-tools-4.18.0-20-generic 
 1748  sudo apt remove linux-tools-generic-hwe-18.04 linux-hwe-tools-4.18.0-20 linux-tools-4.18.0-20-generic linux-tools-common
 1749  sudo apt remove linux-tools-generic-hwe-18.04 linux-hwe-tools-4.18.0-20 linux-tools-4.18.0-20-generic linux-tools-common lsb-release
 1750  sudo apt remove linux-tools-generic-hwe-18.04 linux-hwe-tools-4.18.0-20 linux-tools-4.18.0-20-generic linux-tools-common lsb-release python3
 1751  ./update.sh 
 1752  sudo apt autoremove
 1753  cd /usr/share/python3/runtime.d
 1754  ll
 1755  ll apt-xapian-index.rtupdate 
 1756  sudo update-grub
 1757  ll
 1758  ./monitor-double.sh
 1759  xrandr --help
 1760  xrandr --current
 1761  htop
 1762  ./update.sh 
 1763  ping google.com
 1764  ping 192.168.2.1
 1765  ifconfig 
 1766  ./update.sh 
 1767  sudo apt install distro-info-data
 1768  sudo apt autoremove
 1769  ll /usr/share/applications/
 1770  python3 -V
 1771  sudo apt -y upgrade
 1772  ./update.sh 
 1773  ls -la /usr/bin/python
 1774  sudo apt-get -f install
 1775  python --version
 1776  ll /usr/bin/python
 1777  ll /usr/bin/python2.7
 1778  l /usr/bin/python3
 1779  ll /usr/bin/python3
 1780  ll /usr/bin/python3.6
 1781  ll /usr/bin/python3
 1782  sudo ln -sf /usr/bin/python3.6 /usr/bin/python3
 1783  ll /usr/bin/python3
 1784  sudo apt install lsb-release
 1785  uname -r
 1786  sudo systemctl start NetworkManager
 1787  ping imap.comcast.net
 1788  sudo rm -f /etc/resolv.conf
 1789  sudo ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf
 1790  sudo service systemd-resolved stop
 1791  sudo rm -f /etc/resolv.conf
 1792  sudo ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf
 1793  sudo service systemd-resolved start
 1794  ping imap.comcast.net
 1795  ll /etc/resolv.conf
 1796  sudo systemd-resolve --statistics
 1797  ifconfig
 1798  sudo nano /etc/resolv.conf 
 1799  sudo service systemd-resolved restart
 1800  ping imap.comcast.net
 1801  sudo nano /etc/resolv.conf 
 1802  sudo dhclient -v -4
 1803  ping imap.comcast.net
 1804  ./update.sh 
 1805  sudo apt-get install vlc-plugin-libde265
 1806  sudo apt-get install gstreamer0.10-libde265
 1807  sudo apt-get install gstreamer1.0-libde265
 1808  sudo apt install gstreamer1.0-libav
 1809  93
 1810  ./update.sh 
 1811  synaptic
 1812  gksudo synaptic
 1813  XXXXX
 1814  sudo synaptic
 1815  sudo apt install duplicity 
 1816  ./update.sh 
 1817  sudo apt install gvfs-backends 
 1818  sudo apt install ubuntu-desktop 
 1819  sudo rm /var/lib/apt/lists/lock
 1820  sudo rm /var/lib/dpkg/lock
 1821  sudo rm /var/lib/dpkg/lock-frontend
 1822  sudo dpkg --configure -a
 1823  sudo apt clean
 1824  sudo apt update --fix-missing
 1825  $ sudo apt install -f
 1826  sudo dpkg --configure -a
 1827  cat /etc/apt/sources.list
 1828  ./update.sh 
 1829  sudo apt remove python3
 1830  sudo apt install gir1.2-glib-2.0 python3-gi
 1831  sudo apt purge install-info
 1832  sudo apt purge python3
 1833  sudo apt purge install-info
 1834  sudo apt clean
 1835  sudo apt install python3
 1836  dpkg --info
 1837  dpkg --info apt-xapian-index
 1838  sudo mv /var/lib/dpkg/triggers/File /var/lib/dpkg/triggers/FileEDIT
 1839  sudo mv /var/lib/dpkg/triggers/FileBAK /var/lib/dpkg/triggers/File
 1840  ./update.sh 
 1841  sudo apt install python3
 1842  sudo rm /var/lib/apt/lists/lock
 1843  sudo rm /var/lib/dpkg/lock
 1844  sudo rm /var/lib/dpkg/lock-frontend
 1845  sudo dpkg --configure -a
 1846  sudo apt update --fix-missing
 1847  sudo apt install -f
 1848  sudo dpkg --configure -a
 1849  sudo apt remove 'libgtk2.0-0:i386
 1850  sudo apt remove 'libgtk2.0-0
 1851  sudo apt remove libgtk2.0-0:i386
 1852  ./update.sh 
 1853  sudo apt install libgtk2.0-0:i386
 1854  sudo apt purge libgtk2.0-0:i386
 1855  sudo apt install libgtk2.0-0:i386
 1856  sudo apt update --fix-missing
 1857  dpkg --info apt-xapian-index
 1858  sudo apt install apt-xapian-index
XXXX
 1860  93
 1861  sudo cp -a /var/lib/dpkg/triggers/File /var/lib/dpkg/triggers/FileBAK
 1862  sudo cp -a /var/lib/dpkg/triggers/File /var/lib/dpkg/triggers/FileFUKT
 1863  sudo apt install file
 1864  apt-cache show python3-uno
 1865  cat /var/lib/dpkg/arch
 1866  sudo dpkg --configure -a
 1867  dpkg-query -W -f '"location":"${Filename}","md5":"${MD5sum}","size":"${Size}"\\n'
 1868  uniq -d /var/lib/dpkg/triggers/File
 1869  sort /var/lib/dpkg/triggers/File | uniq -c
 1870  ./update.sh 
 1871  sudo apt install pluseaudio
 1872  sudo dpkg -l|grep pulse
 1873  pkexec gedit /var/lib/dpkg/status
 1874  sudo gedit
 1875  sudo nano  /var/lib/dpkg/status
 1876  sudo dpkg --configure -a
 1877  sudo apt-get -f install
 1878  dpkg --get-selections
 1879  sudo apt purge libgtk2.0-0:i386
 1880  ll /var/lib/dpkg/triggers/File*
 1881  sudo su
 1882  sudo apt install python3
 1883  sudo apt remove python3
 1884  cat .bash_history |grep hwe
 1885  sudo apt install linux-tools-generic-hwe-18.04
 1886  sudo apt purge python3
 1887  gnome-terminal
 1888  sudo apt install python3
 1889  sudo apt install python3 > shm/python3-install.txt
 1890  cat shm/python3-install.txt
 1891  uname -r
 1892  dpkg -v
 1893  dpkg --version
 1894  uname -r
 1895  sudp apt purge python3
 1896  sudo apt purge python3
 1897  sudo apt install python3
 1898  alsamixer
 1899  sudo alsa force-reload
 1900  sudo apt install alsa-base pulseaudio
 1901  sudo apt remove python3
 1902  sudo apt install alsa-base pulseaudio
 1903  sudo alsa force-reload
 1904  ./update.sh 
 1905  sudo apt autoremove
 1906  ./update.sh 
 1907  cat /var/lib/dpkg/triggers/File
 1908  ./speedtest-cli 
 1909  sudo apt-get install apt-xapian-index
 1910  sudo apt-get install -y apt-xapian-index > shm/apt-xapian-index.txt
 1911  ./update.sh 
 1912  sudo apt-get remove apt-xapian-index
 1913  sudo apt-get remove apt-xapian-index python3 
 1914  ./update.sh 
 1915  sudo update-alternatives --config python
 1916  ls /usr/bin | grep python | columns
 1917  update-manager
 1918  sudo apt-get remove python3-apt
 1919  sudo apt-get install python3-apt
 1920  ll /usr/bin/python3.6
 1921  python -V
 1922  python3 -V
 1923  cd /usr/lib/python3/dist-packages
 1924  ll apt_pkg.so
 1925  ll apt_pkg.cpython-36m-x86_64-linux-gnu.so
 1926  ll apt_pkg*
 1927  ll
 1928  cd ~
 1929  sudo apt-get install python-apt
 1930  sudo apt remove python3
 1931  ./update.sh 
 1932  sudo apt autoremove
 1933  sudo apt-get dist-upgrade 
 1934  sudo apt-get update 
 1935  ls /usr/bin | grep python
 1936  sudo apt-get update
 1937  sudo find / -name 'CommandNotFound'
 1938  ll /usr/lib/python3/dist-packages/CommandNotFound
 1939  sudo cp -r /usr/lib/python3/dist-packages/CommandNotFound /usr/lib/
 1940  ./update.sh 
 1941  sudo apt-get update 
 1942  ll /var/lib/command-not-found/
 1943  ll /var/lib/command-not-found
 1944  ll /var/lib/command-not-foun*
 1945  ll /var/lib/command-not-foun
 1946  ll /var/lib/command-not-found
 1947  ll /var/lib/
 1948  ll /usr/lib/python3/dist-packages/CommandNotFound
 1949  sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update --fix-missing
 1950  ll /usr/bin/test
 1951  /usr/bin/test
 1952  /usr/bin/test --help
 1953  cat /usr/bin/test
 1954  cat /var/lib/dpkg/triggers/File
 1955  cat /var/lib/dpkg/triggers/FileBAK 
 1956  sudo cat /var/lib/dpkg/triggers/FileEDIT > /var/lib/dpkg/triggers/File
 1957  sudo -i
 1958  ./update.sh 
 1959  sudo apt-get install python3
 1960  sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update --fix-missing
 1961  sudo apt-get remove python3-apt
 1962  sudo apt-get remove python3
 1963  sudo apt-get remove python3-apt
 1964  cat /var/lib/dpkg/triggers/File
 1965  ./update.sh 
 1966  ll /usr/lib/cnf-update-db
 1967  cat /usr/lib/cnf-update-db
 1968  sudo apt install  python3-apt
 1969  sudo apt install  python3-aptdaemon
 1970  sudo apt install  python3-aptdaemon |grep python3
 1971  sudo apt install  python3-aptdaemon.gtk3widgets |grep python3
 1972  sudo apt install  python3-aptdaemon.pkcompat |grep python3
 1973  sudo apt install python3-aptdaemon.pkcompat
 1974  sudo apt install aptdaemon
 1975  sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update --fix-missing
 1976  ./update.sh 
 1977  sudo apt install python3-aptdaemon.pkcompat
 1978  sudo apt install python3-aptdaemon.gtk3widgets
 1979  ./update.sh 
 1980  ./update.sh 
 1981  sudo aptitude
 1982  sudo find / -name libxapian.so.30
 1983  sudo synaptic
 1984  sudo apt install  libxapian30_1.4.5-1ubuntu0.1_amd64
 1985  sudo apt install  libxapian30_1.4.5-1_i386
 1986  sudo apt install  libxapian30
 1987  sudo synaptic
 1988  sudo aptitude
 1989  ./update.sh 
 1990  dpkg -l | grep ii
 1991  ll /var/backups/dpkg.status.0
 1992  ll /var/lib/dpkg/status
 1993  cd /var/cache/apt/archives/
 1994  ll
 1995  sudo apt-get update --fix-missing
 1996  cd ~
 1997  sudo dpkg --configure -a
 1998  93
 1999  ./update.sh 
 2000  93
 2001  sudo apt --fix-broken install
 2002  sudo apt remove python3
 2003  cat .bash_history |grep remove
 2004  sudo apt remove python3
 2005  sudo apt --fix-broken install
 2006  sudo apt --fix-broken install > shm/fix-broken.txt
 2007  sudo apt remove python3-aptdaemon.gtk3widgets
 2008  history > shm/history
```

---

### Post by dik232 on 2019-06-07
Something else I've found, not sure if it's useful....

```
sudo apt install --reinstall python3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 0 not to upgrade.
10 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for python3:amd64
```

---

### Post by dik232 on 2019-06-11
No ideas?

---

### Post by oldfred on 2019-06-11
Post this to confirm links are correct. This lowercase LL, not II.
ll /usr/bin | grep python

The important links from my 18.04:
```
lrwxrwxrwx  1 root root           9 Apr 16  2018 python -> python2.7*
lrwxrwxrwx  1 root root           9 Apr 16  2018 python2 -> python2.7*
-rwxr-xr-x  1 root root     3670448 Nov 12  2018 python2.7*
lrwxrwxrwx  1 root root           9 Oct 25  2018 python3 -> python3.6*
-rwxr-xr-x  2 root root     4522328 Oct 22  2018 python3.6*

```

---

### Post by dik232 on 2019-06-11
ls -la /usr/bin | grep python


```

lrwxrwxrwx  1 root   root          26 Mar 26  2018 dh_pypy -> ../share/dh-python/dh_pypy-rwxr-xr-x  1 root   root        1056 Apr 16  2018 dh_python2
lrwxrwxrwx  1 root   root          29 Mar 26  2018 dh_python3 -> ../share/dh-python/dh_python3
lrwxrwxrwx  1 root   root          23 Nov 27  2018 pdb2.7 -> ../lib/python2.7/pdb.py
lrwxrwxrwx  1 root   root          23 Nov 12  2018 pdb3.5 -> ../lib/python3.5/pdb.py
lrwxrwxrwx  1 root   root          23 Jan 14 11:02 pdb3.6 -> ../lib/python3.6/pdb.py
lrwxrwxrwx  1 root   root          31 Oct 25  2018 py3versions -> ../share/python3/py3versions.py
lrwxrwxrwx  1 root   root          26 Mar 26  2018 pybuild -> ../share/dh-python/pybuild
lrwxrwxrwx  1 root   root           9 Apr 16  2018 python -> python2.7
lrwxrwxrwx  1 root   root           9 Apr 16  2018 python2 -> python2.7
-rwxr-xr-x  1 root   root     3637680 Nov 27  2018 python2.7
lrwxrwxrwx  1 root   root          33 Nov 12  2018 python2.7-config -> x86_64-linux-gnu-python2.7-config
lrwxrwxrwx  1 root   root          16 Apr 16  2018 python2-config -> python2.7-config
lrwxrwxrwx  1 root   root          25 Jun 11 14:16 python3 -> /etc/alternatives/python3
-rwxr-xr-x  2 root   root     4464368 Nov 12  2018 python3.5
-rwxr-xr-x  2 root   root     4464368 Nov 12  2018 python3.5m
-rwxr-xr-x  2 root   root     4571576 Jan 14 11:02 python3.6
lrwxrwxrwx  1 root   root          33 Oct 22  2018 python3.6-config -> x86_64-linux-gnu-python3.6-config
-rwxr-xr-x  2 root   root     4571576 Jan 14 11:02 python3.6m
lrwxrwxrwx  1 root   root          34 Oct 22  2018 python3.6m-config -> x86_64-linux-gnu-python3.6m-config
lrwxrwxrwx  1 root   root          16 Oct 25  2018 python3-config -> python3.6-config
lrwxrwxrwx  1 root   root          10 Oct 25  2018 python3m -> python3.6m
lrwxrwxrwx  1 root   root          17 Oct 25  2018 python3m-config -> python3.6m-config
-rwxr-xr-x  1 root   root        1797 Jul 12  2017 python3-unidiff
lrwxrwxrwx  1 root   root          16 Apr 16  2018 python-config -> python2.7-config
lrwxrwxrwx  1 root   root          29 Apr 16  2018 pyversions -> ../share/python/pyversions.py
-rwxr-xr-x  1 root   root        2975 Nov 12  2018 x86_64-linux-gnu-python2.7-config
lrwxrwxrwx  1 root   root          34 Oct 22  2018 x86_64-linux-gnu-python3.6-config -> x86_64-linux-gnu-python3.6m-config
-rwxr-xr-x  1 root   root        3283 Oct 22  2018 x86_64-linux-gnu-python3.6m-config
lrwxrwxrwx  1 root   root          33 Oct 25  2018 x86_64-linux-gnu-python3-config -> x86_64-linux-gnu-python3.6-config
lrwxrwxrwx  1 root   root          34 Oct 25  2018 x86_64-linux-gnu-python3m-config -> x86_64-linux-gnu-python3.6m-config
lrwxrwxrwx  1 root   root          33 Apr 16  2018 x86_64-linux-gnu-python-config -> x86_64-linux-gnu-python2.7-config



```

---

### Post by oldfred on 2019-06-11
This in not the normal version.
python3 -> /etc/alternatives/python3

If you want alternative versions you keep them separate.
Link should be to
python3 -> python3.6*

---

### Post by dik232 on 2019-06-12
Yes, that's a possible fix I was trying yesterday that didn't work.  You can see the date Jun 11

Have now reverted 

```

ls -la /usr/bin/python3
lrwxrwxrwx 1 root root 9 Jun 12 11:04 /usr/bin/python3 -> python3.6

```

---

### Post by dik232 on 2019-06-14
No other ideas?

---

