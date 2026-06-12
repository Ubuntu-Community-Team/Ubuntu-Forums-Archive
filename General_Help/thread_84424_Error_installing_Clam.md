---
title: "Error installing Clam"
date: 2005-10-31
forum: General Help
---

### Post by Doc.Caliban on 2005-10-31
Not sure where to go from here:

$apt-get install clamav
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  clamav-base clamav-freshclam libclamav1 libgmp3c2 libgmpxx3
Suggested packages:
  unrar lha clamav-docs
Recommended packages:
  arj unzoo
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam libclamav1 libgmp3c2 libgmpxx3
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 3651kB of archives.
After unpacking 4764kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libgmpxx3 4.1.4-10ubuntu1 [171kB]Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libgmp3c2 4.1.4-10ubuntu1 [314kB]Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe libclamav1 0.87-1 [256kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe clamav-base 0.87-1 [166kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe clamav-freshclam 0.87-1 [2680kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe clamav 0.87-1 [64.8kB]
Fetched 3651kB in 2m24s (25.2kB/s)

Preconfiguring packages ...
Selecting previously deselected package libgmpxx3.
(Reading database ... 59539 files and directories currently installed.)
Unpacking libgmpxx3 (from .../libgmpxx3_4.1.4-10ubuntu1_i386.deb) ...
Selecting previously deselected package libgmp3c2.
Unpacking libgmp3c2 (from .../libgmp3c2_4.1.4-10ubuntu1_i386.deb) ...
Selecting previously deselected package libclamav1.
Unpacking libclamav1 (from .../libclamav1_0.87-1_i386.deb) ...
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.87-1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.87-1_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.87-1_i386.deb) ...
Setting up clamav-base (0.87-1) ...
Adding system user `clamav'...
Adding new group `clamav' (114).
Adding new user `clamav' (114) with group `clamav'.
Not creating home directory.
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (= 0.87-1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Setting up libgmpxx3 (4.1.4-10ubuntu1) ...

Setting up libgmp3c2 (4.1.4-10ubuntu1) ...

Setting up libclamav1 (0.87-1) ...

Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by suRoot on 2005-10-31
[QUOTE=Doc.Caliban]$apt-get install clamav[/QUOTE]

Why are you not running this as root or sudo?

It looks like it's crashing after adding trying to add users & groups.

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=suRoot]Why are you not running this as root or sudo?[/QUOTE]

Days of Windows experience: ~6,000
Days of Linux experience: 2

That fixed it, thanks!

-Doc

---

### Post by neobloodline on 2005-12-04
I had the same problem even using sudo.. could anyone help me..please

---

