---
title: "python version stays at 2.6.8 on ubuntu 12.04"
date: 2013-08-11
forum: General Help
---

### Post by taopublic on 2013-08-11
Hi, I googled and it seems that we should have 2.7.3 on precise, however, i still have 2.6.8.

python --version
Python 2.6.8

python
Python 2.6.8 (unknown, Apr 27 2012, 11:55:38) 
[GCC 4.6.3] on linux3
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.path
['', '/usr/local/stow/Python-2.6.8/lib/python26.zip', '/usr/local/stow/Python-2.6.8/lib/python2.6', '/usr/local/stow/Python-2.6.8/lib/python2.6/plat-linux3', '/usr/local/stow/Python-2.6.8/lib/python2.6/lib-tk', '/usr/local/stow/Python-2.6.8/lib/python2.6/lib-old', '/usr/local/stow/Python-2.6.8/lib/python2.6/lib-dynload', '/usr/local/stow/Python-2.6.8/lib/python2.6/site-packages']

I don't use python directly but the problem is that some software packages, e.g. PlayOnLinux, seem to assume python 2.7 is installed. Can someone tell me why my python version is wrong? I obviously didn't manually upgrade/downgrade python on my box. I installed ubuntu 12.04 from scratch last year. Is there any way to fix this? Fyi, here is the error I got when running PlayOnLinux,

playonlinux
Traceback (most recent call last):
  File "mainwindow.py", line 30, in <module>
    import wx
ImportError: No module named wx
Traceback (most recent call last):
  File "mainwindow.py", line 30, in <module>
    import wx
ImportError: No module named wx

---

### Post by taopublic on 2013-08-11
Correction, it seems that I do have python 2.7, but it is not the default interpreter.

ls -ld /usr/lib/python*
drwxr-xr-x  3 root root  4096 Aug 10 23:08 /usr/lib/python2.6
drwxr-xr-x 26 root root 24576 Jul  1 22:02 /usr/lib/python2.7
drwxr-xr-x  3 root root  4096 Mar 15  2012 /usr/lib/python3
drwxr-xr-x 31 root root 12288 Aug 10 22:29 /usr/lib/python3.2
drwxr-xr-x  2 root root  4096 Aug 10 23:40 /usr/lib/python-tz

Anyway to change to 2.7 for default?

---

### Post by Cheesemill on 2013-08-11
Can you post the output of the following commands to try and give us a clue what's happening...
```
apt-cache show python
dpkg --get-selections | grep python
which python
sudo apt-get -y -s install python

```

---

### Post by Cheesemill on 2013-08-11
Can you post the output of the following commands to try and give us a clue what's happening...
```
apt-cache show python
dpkg --get-selections | grep python
which python
update-alternatives --display python
sudo apt-get -y -s install python

```

---

### Post by Cheesemill on 2013-08-11
Just seen your 2nd post.

Run this...
```
sudo update-alternatives --config python
```

---

### Post by taopublic on 2013-08-11
thanks for the quick reply, the sudo update-alternatives --config python command didn't work, here is the output,

```
sudo update-alternatives --config python
update-alternatives: error: no alternatives for python.

```

Here is the output of the diagnosis commands,

Strangely this command shows I have 2.7 installed
```
sudo apt-cache show python
Package: python
Priority: important
Section: python
Installed-Size: 658
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Architecture: amd64
Source: python-defaults
Version: 2.7.3-0ubuntu2.2
Replaces: python-dev (<< 2.6.5-2)
Provides: python-ctypes, python-email, python-importlib, python-profiler, python-wsgiref
Depends: python2.7 (>= 2.7.3), python-minimal (= 2.7.3-0ubuntu2.2)
Suggests: python-doc (= 2.7.3-0ubuntu2.2), python-tk (= 2.7.3-0ubuntu2.2)
Conflicts: python-central (<< 0.5.5)
Breaks:  python-bz2 (<< 1.1-8), python-csv (<< 1.0-4), python-email  (<< 2.5.5-3), update-manager-core (<< 0.200.5-2)
Filename: pool/main/p/python-defaults/python_2.7.3-0ubuntu2.2_amd64.deb
Size: 167552
MD5sum: 81b302b2f98d8125fa60a886a61644fe
SHA1: 336fcd82246e00f52455112dba780fa34cb0eaa8
SHA256: bec692c0b1629e68002b317d3bcef0e6234d723d7aafcec5e0d81eb94449b76c
Description-en: interactive high-level object-oriented language (default version)
 Python, the high-level, interactive object oriented language,
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
 .
 This package is a dependency package, which depends on Debian's default
 Python version (currently v2.7).
Multi-Arch: allowed
Homepage: http://www.python.org/
Description-md5: d1ea97f755d8153fe116080f2352859b
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: minimal

Package: python
Priority: important
Section: python
Installed-Size: 658
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Architecture: amd64
Source: python-defaults
Version: 2.7.3-0ubuntu2
Replaces: python-dev (<< 2.6.5-2)
Provides: python-ctypes, python-email, python-importlib, python-profiler, python-wsgiref
Depends: python2.7 (>= 2.7.3), python-minimal (= 2.7.3-0ubuntu2)
Suggests: python-doc (= 2.7.3-0ubuntu2), python-tk (= 2.7.3-0ubuntu2)
Conflicts: python-central (<< 0.5.5)
Breaks:  python-bz2 (<< 1.1-8), python-csv (<< 1.0-4), python-email  (<< 2.5.5-3), update-manager-core (<< 0.200.5-2)
Filename: pool/main/p/python-defaults/python_2.7.3-0ubuntu2_amd64.deb
Size: 166114
MD5sum: 5e0615e173a3834d0b2e97768bfe4d2c
SHA1: a748ba4f38c3dd94bc6d782a8421499b01c406f3
SHA256: ec8a24ec3cf3dfdf42581fa529e0ee69dc08bd8c29aeb601c329c337e5605e0e
Description-en: interactive high-level object-oriented language (default version)
 Python, the high-level, interactive object oriented language,
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
 .
 This package is a dependency package, which depends on Debian's default
 Python version (currently v2.7).
Homepage: http://www.python.org/
Description-md5: d1ea97f755d8153fe116080f2352859b
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: minimal

```

Again, it shows 2.7 is installed
```
dpkg --get-selections | grep python
libpython2.7                    install
libpython3.2                    deinstall
python                        install
python-appindicator                install
python-apport                    install
python-apt                    install
python-apt-common                install
python-aptdaemon                install
python-aptdaemon.gtk3widgets            install
python-aptdaemon.pkcompat            install
python-beautifulsoup                install
python-brlapi                    install
python-cairo                    install
python-central                    install
python-chardet                    install
python-configglue                install
python-configobj                install
python-configshell                install
python-crypto                    install
python-cups                    install
python-cupshelpers                install
python-dateutil                    install
python-dbus                    install
python-dbus-dev                    install
python-debian                    install
python-debtagshw                install
python-defer                    install
python-dev                    install
python-dirspec                    install
python-docutils                    install
python-egenix-mxdatetime            install
python-egenix-mxtools                install
python-epydoc                    install
python-feedparser                install
python-gconf                    install
python-gdbm                    install
python-gi                    install
python-gi-cairo                    install
python-glade2                    install
python-gmenu                    install
python-gnomekeyring                install
python-gnupginterface                install
python-gobject                    install
python-gobject-2                install
python-gst0.10                    install
python-gtk2                    install
python-html2text                install
python-httplib2                    install
python-ibus                    install
python-imaging                    install
python-keyring                    install
python-launchpadlib                install
python-lazr.restfulclient            install
python-lazr.uri                    install
python-libproxy                    install
python-libxml2                    install
python-louis                    install
python-lxml                    install
python-magic                    install
python-mako                    install
python-markupsafe                install
python-minimal                    install
python-mlt3                    install
python-notify                    install
python-numpy                    install
python-oauth                    install
python-oauth2                    install
python-openssl                    install
python-packagekit                install
python-pam                    install
python-pexpect                    install
python-piston-mini-client            install
python-pkg-resources                install
python-problem-report                install
python-protobuf                    install
python-pyatspi2                    install
python-pycurl                    install
python-pygments                    install
python-pygoocanvas                install
python-pyinotify                install
python-pyside.qtcore                install
python-pyside.qtgui                install
python-pyside.qtnetwork                install
python-pyside.qtwebkit                install
python-pysqlite2                install
python-regex                    install
python-renderpm                    install
python-reportlab                install
python-reportlab-accel                install
python-roman                    install
python-scour                    install
python-serial                    install
python-simplejson                install
python-simpleparse                install
python-simpleparse-mxtexttools            install
python-smbc                    install
python-software-properties            install
python-speechd                    install
python-sqlalchemy                install
python-sqlalchemy-ext                install
python-support                    install
python-tk                    install
python-twisted-bin                install
python-twisted-core                install
python-twisted-names                install
python-twisted-web                install
python-tz                    install
python-ubuntu-sso-client            install
python-ubuntuone-client                install
python-ubuntuone-control-panel            install
python-ubuntuone-storageprotocol        install
python-unity-singlet                install
python-uno                    install
python-utidylib                    install
python-virtkey                    install
python-wadllib                    install
python-wxgtk2.8                    install
python-wxversion                install
python-xapian                    install
python-xdg                    install
python-xkit                    install
python-zeitgeist                install
python-zope.interface                install
python2.7                    install
python2.7-dev                    install
python2.7-minimal                install
python3                        install
python3-minimal                    install
python3.2                    install
python3.2-minimal                install

```

However, my binary is 2.6.8?
```
which python
/usr/local/bin/python

ls -l /usr/local/bin/python
lrwxrwxrwx 1 root root 31 Feb 11 17:03 /usr/local/bin/python -> ../stow/Python-2.6.8/bin/python
```

```
sudo update-alternatives --display python
update-alternatives: error: no alternatives for python.
```

```

sudo apt-get -y -s install python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Is this a case of failed update? Is there any way for me to fix this? Thanks!

---

### Post by Cheesemill on 2013-08-11
It looks like at some point you must have used the program [stow]("http://www.gnu.org/software/stow/") to install version 2.6.8 of Python in it's own directory and create the symlinks so that appears as the native version.

This should get rid of it...
```
cd /usr/local/bin/stow
sudo stow --delete Python-2.6.8
```

---

### Post by taopublic on 2013-08-11
That fixed my problem. Thanks a lot!

---

