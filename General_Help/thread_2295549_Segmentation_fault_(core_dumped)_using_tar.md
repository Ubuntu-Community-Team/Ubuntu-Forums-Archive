---
title: "Segmentation fault (core dumped) using tar"
date: 2015-09-19
forum: General Help
---

### Post by juliushibert63 on 2015-09-19
I'm getting a Segmentation fault (core dumped) error whenever using tar.

```
$ tar -xvf CrashPlan_4.3.0_Linux.tgz
Segmentation fault (core dumped)
```

I've tried reinstalling tar but still no such luck and I can;t seem to find any solutuion outside a dist-upgrade or a reinstall of tar. Which both don't seem to work.

```
$ sudo apt-get install --reinstall tarReading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 13 not upgraded.
Need to get 0 B/171 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg-deb: error: subprocess tar was killed by signal (Segmentation fault), core dumped
dpkg: error processing archive /var/cache/apt/archives/tar_1.27.1-1_armhf.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.27.1-1_armhf.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dragonfly41 on 2015-09-19
On occasions I have used the tip I read in this post ..

[https://bugs.launchpad.net/bzr-gtk/+bug/923824](https://bugs.launchpad.net/bzr-gtk/+bug/923824)

to find source of elusive segmentation faults.

> 

I advise to temporarily modify /usr/lib/python2.7/dist-packages/gobject/constants.py to say

raise ImportError("no static plz")

somewhere at the top, then you will get a proper backtrace and can easily identify the culprit.



---

### Post by tgalati4 on 2015-09-19
Check the SMART status of your hard drive.  Two seg faults with two different programs (tar and dpkg) is troubling.

```
sudo smartctl -a /dev/sda
```

A failing hard disk can cause unusual errors.

---

### Post by juliushibert63 on 2015-09-19
> **tgalati4 said:**
> Check the SMART status of your hard drive.  Two seg faults with two different programs (tar and dpkg) is troubling.

```
sudo smartctl -a /dev/sda
```

A failing hard disk can cause unusual errors.

I don't have smartctl installed. Running `sudo apt-get install smartmontools` produces the same errors with tar:

```
$ sudo apt-get install smartmontools -yReading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  heirloom-mailx
Suggested packages:
  gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  heirloom-mailx smartmontools
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 608 kB of archives.
After this operation, 1,630 kB of additional disk space will be used.
Get:1 http://ports.ubuntu.com/ubuntu-ports/ trusty-updates/universe heirloom-mailx armhf 12.5-2+deb7u1build0.14.04.1 [193 kB]
Get:2 http://ports.ubuntu.com/ubuntu-ports/ trusty/main smartmontools armhf 6.2+svn3841-1.2 [415 kB]
Fetched 608 kB in 0s (1,262 kB/s)
dpkg-deb: error: subprocess tar was killed by signal (Segmentation fault), core dumped
dpkg: error processing archive /var/cache/apt/archives/heirloom-mailx_12.5-2+deb7u1build0.14.04.1_armhf.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: subprocess tar was killed by signal (Segmentation fault), core dumped
dpkg: error processing archive /var/cache/apt/archives/smartmontools_6.2+svn3841-1.2_armhf.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/heirloom-mailx_12.5-2+deb7u1build0.14.04.1_armhf.deb
 /var/cache/apt/archives/smartmontools_6.2+svn3841-1.2_armhf.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 



> **dragonfly41 said:**
> On occasions I have used the tip I read in this post ..

[https://bugs.launchpad.net/bzr-gtk/+bug/923824](https://bugs.launchpad.net/bzr-gtk/+bug/923824)

to find source of elusive segmentation faults.

I've updated my `/usr/lib/python2.7/dist-packages/gobject/constants.py` file as suggested but I don't appear to be getting any more detailed debug output. Is this correct for the formatting of `/usr/lib/python2.7/dist-packages/gobject/constants.py`?

```
$ cat /usr/lib/python2.7/dist-packages/gobject/constants.py
# -*- Mode: Python; py-indent-offset: 4 -*-
# pygobject - Python bindings for the GObject library
# Copyright (C) 2006-2007 Johan Dahlin
#
#   gobject/constants.py: GObject type constants
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301
# USA


import sys


import gobject._gobject
raise ImportError("no static plz")
_gobject = sys.modules['gobject._gobject']


# TYPE_INVALID defined in gobjectmodule.c
TYPE_NONE = _gobject.type_from_name('void')
TYPE_INTERFACE = _gobject.type_from_name('GInterface')
TYPE_CHAR = _gobject.type_from_name('gchar')
TYPE_UCHAR = _gobject.type_from_name('guchar')
TYPE_BOOLEAN = _gobject.type_from_name('gboolean')
TYPE_INT = _gobject.type_from_name('gint')
TYPE_UINT = _gobject.type_from_name('guint')
TYPE_LONG = _gobject.type_from_name('glong')
TYPE_ULONG = _gobject.type_from_name('gulong')
TYPE_INT64 = _gobject.type_from_name('gint64')
TYPE_UINT64 = _gobject.type_from_name('guint64')
TYPE_ENUM = _gobject.type_from_name('GEnum')
TYPE_FLAGS = _gobject.type_from_name('GFlags')
TYPE_FLOAT = _gobject.type_from_name('gfloat')
TYPE_DOUBLE = _gobject.type_from_name('gdouble')
TYPE_STRING = _gobject.type_from_name('gchararray')
TYPE_POINTER = _gobject.type_from_name('gpointer')
TYPE_BOXED = _gobject.type_from_name('GBoxed')
TYPE_PARAM = _gobject.type_from_name('GParam')
TYPE_OBJECT = _gobject.type_from_name('GObject')
TYPE_PYOBJECT = _gobject.type_from_name('PyObject')
TYPE_UNICHAR = TYPE_UINT


# do a little dance to maintain API compatibility
# as these were origianally defined here, and are
# now defined in gobjectmodule.c
G_MINFLOAT = _gobject.G_MINFLOAT
G_MAXFLOAT = _gobject.G_MAXFLOAT
G_MINDOUBLE = _gobject.G_MINDOUBLE
G_MAXDOUBLE = _gobject.G_MAXDOUBLE
G_MINSHORT = _gobject.G_MINSHORT
G_MAXSHORT = _gobject.G_MAXSHORT
G_MAXUSHORT = _gobject.G_MAXUSHORT
G_MININT = _gobject.G_MININT
G_MAXINT = _gobject.G_MAXINT
G_MAXUINT = _gobject.G_MAXUINT
G_MINLONG = _gobject.G_MINLONG
G_MAXLONG = _gobject.G_MAXLONG
G_MAXULONG = _gobject.G_MAXULONG
G_MININT8 = _gobject.G_MININT8
G_MAXINT8 = _gobject.G_MAXINT8
G_MAXUINT8 = _gobject.G_MAXUINT8
G_MININT16 = _gobject.G_MININT16
G_MAXINT16 = _gobject.G_MAXINT16
G_MAXUINT16 = _gobject.G_MAXUINT16
G_MININT32 = _gobject.G_MININT32
G_MAXINT32 = _gobject.G_MAXINT32
G_MAXUINT32 = _gobject.G_MAXUINT32
G_MININT64 = _gobject.G_MININT64
G_MAXINT64 = _gobject.G_MAXINT64
G_MAXUINT64 = _gobject.G_MAXUINT64
G_MAXSIZE = _gobject.G_MAXSIZE
G_MAXSSIZE = _gobject.G_MAXSSIZE
G_MINOFFSET = _gobject.G_MINOFFSET
G_MAXOFFSET = _gobject.G_MAXOFFSET
```

---

### Post by tgalati4 on 2015-09-19
So *tar* is borked and *tar* is required to unpack Debian packages--so it really is a single problem.

```
which tar
```

It should be /usr/bin/tar

Simply delete the old *tar* binary and copy another *tar* binary from another machine of the same distro.  Strange problem requires an equally strange solution.

---

### Post by juliushibert63 on 2015-09-19
Thankfully I have an exact same system with the same tar packaged. Deleting and copying it from a working system fixed the segmentation error.

---

### Post by tgalati4 on 2015-09-19
Well, that is good.  Yes, there are times that a part of the system will break that is not easily repairable.  

Now perform some housecleaning:

```
sudo apt-get clean
sudo apt-get check
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```

Don't forget to check your drive's SMART status, in case there really is a hardware problem.

---

### Post by jim_deadlock on 2015-09-20
Just a thought, but have you tried

```
tar -xvfz CrashPlan_4.3.0_Linux.tgz
```
It's a compressed file so perhaps you need the z option?

---

### Post by juliushibert63 on 2015-09-20
> **tgalati4 said:**
> Well, that is good.  Yes, there are times that a part of the system will break that is not easily repairable.  

Now perform some housecleaning:

```
sudo apt-get clean
sudo apt-get check
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```

Don't forget to check your drive's SMART status, in case there really is a hardware problem.

As this is a BananaPi SBC box, the boot disk is an SD card. I'm not really sure what drive type this would fall under or even if it has SMART.

```
$ sudo smartctl -a /dev/mmcblk0smartctl 6.2 2013-07-26 r3841 [armv7l-linux-3.4.103] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


/dev/mmcblk0: Unable to detect device type
Please specify device type with the -d option.


Use smartctl -h to get a usage summary
```

---

### Post by tgalati4 on 2015-09-20
Well, SD cards do have a habit of failing when used as an active file system.  Keep your eye on it.  If you get other weirdness, then it is time to change the card.

---

