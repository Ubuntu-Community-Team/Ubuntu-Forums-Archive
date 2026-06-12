---
title: "Issue with libtorrent"
date: 2014-07-10
forum: General Help
---

### Post by KBoisits on 2014-07-10
I recently upgraded from ubuntu 12.04 to ubuntu 14.04. After the upgrade deluged would not run with this output:

```
[ERROR   ] 23:05:44 main:237 libboost_system.so.1.46.1: cannot open shared object file: No such file or directoryTraceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/deluge-1.3.6-py2.7.egg/deluge/main.py", line 230, in start_daemon
    Daemon(options, args)
  File "/usr/lib/python2.7/dist-packages/deluge-1.3.6-py2.7.egg/deluge/core/daemon.py", line 136, in __init__
    from deluge.core.core import Core
  File "/usr/lib/python2.7/dist-packages/deluge-1.3.6-py2.7.egg/deluge/core/core.py", line 36, in <module>
    from deluge._libtorrent import lt
  File "/usr/lib/python2.7/dist-packages/deluge-1.3.6-py2.7.egg/deluge/_libtorrent.py", line 59, in <module>
    import libtorrent as lt
ImportError: libboost_system.so.1.46.1: cannot open shared object file: No such file or directory
```

I tried to remove python-libtorrent and after instaling it again I get the same error. I believe previously I manually built libtorrent for use with deluge.

Thanks,
  Kevin

---

### Post by slooksterpsv on 2014-07-10
When you removed it, did you try using:

sudo apt-get purge *package_name*

I'd try that, and also make sure you have this one installed as it's a dependency:

libboost-system1.54.0

---

### Post by KBoisits on 2014-07-10
I confirmed that libboost-system1.54.0 is installed and also purged and reinstalled libtorrent. But am still getting the same error. Get the same error when I run this as I was trying to determine the version I have installed:

sudo python -c "import libtorrent as lt; print lt.version"

Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: libboost_system.so.1.46.1: cannot open shared object file: No such file or directory

Thanks,
  Kevin

---

### Post by slooksterpsv on 2014-07-10
You could rebuild that specific version, it may need just 1.46 - but isn't deluge in the repositories? Or would you consider using a PPA for it?

---

### Post by KBoisits on 2014-07-10
According to [http://packages.ubuntu.com/trusty/python-libtorrent](http://packages.ubuntu.com/trusty/python-libtorrent) this package should require 1.54. I assume it has something to do with me manually building libtorrent previously and there is something that I am not removing. I did uninstall and go through and delete some files to try to correct this. But still getting the same thing after I reinstall.

How would I go about installing or building boost 1.46.1?

When I try this: ```
sudo apt-get install libboost-system1.46.1
```

I get: ```
Package libboost-system1.46.1 is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libboost-system1.46.1' has no installation candidate

```

---

### Post by slooksterpsv on 2014-07-10
[http://packages.ubuntu.com/precise/libboost-system1.46.1](http://packages.ubuntu.com/precise/libboost-system1.46.1)

You could TRY to install the DEB from here, it may mess up things though where it's an older piece of software.

---

### Post by KBoisits on 2014-07-13
How do you install from the DEB?

---

### Post by slooksterpsv on 2014-07-13
Download your architecture, it'll download the DEB file, just double click and Software Center will open it. You can also install it via terminal with sudo dpkg -i ./*file_name_of_deb_you_downloaded.deb*

---

### Post by KBoisits on 2014-07-14
This got it working sort of, but was getting other errors because I assume it was expecting a different version. But finally got it working bu removing libtorrent and then manually deleting a lot of files and reinstalling deluged. Hopefully I didn't delete too much and everything else will still be working..

Thanks for your help.

---

