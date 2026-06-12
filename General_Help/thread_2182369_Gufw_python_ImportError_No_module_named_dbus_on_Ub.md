---
title: "Gufw python ImportError: No module named dbus on Ubuntu precise 12.04 LTS Amd64"
date: 2013-10-21
forum: General Help
---

### Post by cpad on 2013-10-21
When trying to run Gufw on my Ubuntu precise 12.04 LTS Amd64 WS, I got the following python error:
ImportError: No module named dbus

[INDENT][B]gufw 
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gufw/gufw.py", line 20, in <module>
    from controller   import Controller 
  File "/usr/share/pyshared/gufw/controller.py", line 18, in <module>
    from model.Firewall import Firewall
  File "/usr/share/pyshared/gufw/model/Firewall.py", line 22, in <module>
[COLOR=#ff0000]  [/COLOR]  import dbus[COLOR=#ff0000]
ImportError: No module named dbus[/COLOR][/B]
[/INDENT]

I've checked which python version installed and found 2.7.3


[INDENT][B]sudo apt-cache show python
Package: python
Priority: important
Section: python
Installed-Size: 658
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Architecture: amd64
Source: python-defaults
[COLOR=#ff0000]Version: 2.7.3-0ubuntu2.2[/COLOR]
Replaces: python-dev (<< 2.6.5-2)
Provides: python-ctypes, python-email, python-importlib, python-profiler, python-wsgiref
Depends: python2.7 (>= 2.7.3), python-minimal (= 2.7.3-0ubuntu2.2)
Suggests: python-doc (= 2.7.3-0ubuntu2.2), python-tk (= 2.7.3-0ubuntu2.2)
Conflicts: python-central (<< 0.5.5)
Breaks: python-bz2 (<< 1.1-8), python-csv (<< 1.0-4), python-email (<< 2.5.5-3), update-manager-core (<< 0.200.5-2)
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
Homepage: [http://www.python.org/](http://www.python.org/)
Description-md5: d1ea97f755d8153fe116080f2352859b
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
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
Breaks: python-bz2 (<< 1.1-8), python-csv (<< 1.0-4), python-email (<< 2.5.5-3), update-manager-core (<< 0.200.5-2)
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
Homepage: [http://www.python.org/](http://www.python.org/)
Description-md5: d1ea97f755d8153fe116080f2352859b
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: minimal[/B]
[/INDENT]

I also cheched that python-dbus is installed 


[INDENT][B]dpkg --get-selections | grep python
libpython2.7                    install
libpython3.2                    deinstall
python                        install
python-appindicator                install
python-apport                    install
python-apt                    install
python-apt-common                install
python-aptdaemon                install
python-aptdaemon-gtk                install
python-aptdaemon.gtk3widgets            install
python-aptdaemon.gtkwidgets            install
python-aptdaemon.pkcompat            install
python-brlapi                    install
python-cairo                    install
python-central                    install
python-chardet                    install
python-configglue                install
python-configobj                install
python-crypto                    install
python-cups                    install
python-cupshelpers                install
python-dateutil                    install
[COLOR=#ff0000]python-dbus                    install
python-dbus-dev                    install[/COLOR]
python-debian                    install
python-debtagshw                install
python-defer                    install
python-dev                    install
python-dirspec                    install
python-egenix-mxdatetime            install
python-egenix-mxtools                install
python-gconf                    install
python-gdbm                    install
python-gi                    install
python-gi-cairo                    install
python-glade2                    install
python-gmenu                    install
python-gnome2                    install
python-gnomekeyring                install
python-gnupginterface                install
python-gobject                    install
python-gobject-2                install
python-gobject-2-dev                install
python-gst0.10                    install
python-gtk2                    install
python-httplib2                    install
python-ibus                    install
python-imaging                    install
python-indicate                    install
python-keyring                    install
python-launchpad-integration            install
python-launchpadlib                install
python-lazr.restfulclient            install
python-lazr.uri                    install
python-libproxy                    install
python-libuser                    install
python-libxml2                    install
python-louis                    install
python-lxml                    install
python-mako                    install
python-markupsafe                install
python-minimal                    install
python-notify                    install
python-numpy                    install
python-oauth                    install
python-openssl                    install
python-packagekit                install
python-pam                    install
python-pexpect                    install
python-piston-mini-client            install
python-pkg-resources                install
python-poppler                    install
python-problem-report                install
python-protobuf                    install
python-pyatspi2                    install
python-pycurl                    install
python-pygoocanvas                install
python-pyinotify                install
python-pyorbit                    install
python-pypdf                    install
python-qt4                    install
python-qt4-dbus                    install
python-renderpm                    install
python-reportlab                install
python-reportlab-accel                install
python-serial                    install
python-simplejson                install
python-sip                    install
python-smbc                    install
python-software-properties            install
python-speechd                    install
python-support                    install
python-telepathy                install
python-tk                    install
python-twisted-bin                install
python-twisted-core                install
python-twisted-names                install
python-twisted-web                install
python-ubuntu-sso-client            install
python-ubuntuone-client                install
python-ubuntuone-control-panel            install
python-ubuntuone-storageprotocol        install
python-uniconvertor                install
python-uno                    install
python-virtkey                    install
python-vte                    install
python-wadllib                    install
python-webkit                    install
python-wnck                    install
python-wxversion                install
python-xapian                    install
python-xdg                    install
python-xkit                    install
python-zeitgeist                install
python-zope.interface                install
python2.7                    install
python2.7-dev                    install
python2.7-minimal                install
python3.2                    deinstall
python3.2-minimal                deinstall[/B]
[/INDENT]

Any idea on how to fix that issue ???

Thanks



[INDENT]
[/INDENT]

---

