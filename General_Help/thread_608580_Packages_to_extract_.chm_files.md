---
title: "Packages to extract .chm files"
date: 2007-11-10
forum: General Help
---

### Post by satimis on 2007-11-10
Hi folks,


Ubuntu 7.04 desktop


I need to convet .chm as .html/.pdf.  I have libchm and htmldoc installed.  But can't convert .chm files as described on;

How to Convert chm files to HTML or PDF files
[http://www.ubuntugeek.com/how-to-convert-chm-files-to-html-or-pdf-files.html](http://www.ubuntugeek.com/how-to-convert-chm-files-to-html-or-pdf-files.html)


Are there better packages for doing the job.  Which package is .chm viewer? xchm?


TIA


B.R.
satimis

---

### Post by scorp123 on 2007-11-10
> **satimis said:**
>   Which package is .chm viewer?  Try this one: **gnochm** .... It's available via Synaptic. ```
apt-cache show gnochm
Package: gnochm
Priority: optional
Section: universe/gnome
...
Description: CHM file viewer for GNOME
 Gnochm is a Compiled HTML Help (CHM) file viewer for GNOME systems.
 .
 Features are:
  * Support for external ms-its links
  * Full text search support
  * Bookmarks
  * Configurable support for HTTP links
  * Integrated with GNOME2
  * Support for multiple languages
  * Support to open multiple files at once
 .
 Homepage: http://gnochm.sourceforge.net/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by satimis on 2007-11-10
> **scorp123 said:**
> Try this one: **gnochm** .... It's available via Synaptic. ```
apt-cache show gnochm
Package: gnochm
Priority: optional
Section: universe/gnome
...
Description: CHM file viewer for GNOME
 Gnochm is a Compiled HTML Help (CHM) file viewer for GNOME systems.
 .
 Features are:
  * Support for external ms-its links
  * Full text search support
  * Bookmarks
  * Configurable support for HTTP links
  * Integrated with GNOME2
  * Support for multiple languages
  * Support to open multiple files at once
 .
 Homepage: http://gnochm.sourceforge.net/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```
Thanks for your advice.

I'm running Fluxbox, a light-weight desktop.  I don't have gnome packages installed because this is a server.  I'm worring installing gnchm will pull other gnome packages.


B.R.
satimis

---

### Post by scorp123 on 2007-11-10
> **satimis said:**
>  I'm worring installing gnchm will pull other gnome packages. Simulate it and then see what it suggests. ```
sudo apt-get --simulate install gnochm
```

According to the info I have (from "dpkg -s gnochm") it only depends on few packages: 
```
Package: gnochm
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 760
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: all
Version: 0.9.9-0ubuntu1
[B][COLOR="RoyalBlue"]Depends: gconf2 (>= 2.12.1-4ubuntu1), scrollkeeper (>= 0.3.8), 
python-gtk2 (>= 2.8.2), python-glade2 (>= 2.2.0), python-gnome2, 
python-gnome2-extras, python-chm (>= 0.8.2-2), shared-mime-info[/COLOR][/B]
Recommends: python-cjkcodecs
Description: CHM file viewer for GNOME
 Gnochm is a Compiled HTML Help (CHM) file viewer for GNOME systems.
 .
 Features are:
  * Support for external ms-its links
  * Full text search support
  * Bookmarks
  * Configurable support for HTTP links
  * Integrated with GNOME2
  * Support for multiple languages
  * Support to open multiple files at once
 .
 Homepage: http://gnochm.sourceforge.net/
Original-Maintainer: Carlos Z.F. Liu <carlosliu@users.sourceforge.net>
```

... But you are right, those few (especially "gconf") could pull a lot more dependencies. So your best bet would probably be to run through an "apt-get --simulate" and see what would happen before it really does happen.

---

### Post by satimis on 2007-11-11
> **scorp123 said:**
> Simulate it and then see what it suggests. ```
sudo apt-get --simulate install gnochm
```

According to the info I have (from "dpkg -s gnochm") it only depends on few packages: 
```
Package: gnochm
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 760
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: all
Version: 0.9.9-0ubuntu1
[B][COLOR="RoyalBlue"]Depends: gconf2 (>= 2.12.1-4ubuntu1), scrollkeeper (>= 0.3.8), 
python-gtk2 (>= 2.8.2), python-glade2 (>= 2.2.0), python-gnome2, 
python-gnome2-extras, python-chm (>= 0.8.2-2), shared-mime-info[/COLOR][/B]
Recommends: python-cjkcodecs
Description: CHM file viewer for GNOME
 Gnochm is a Compiled HTML Help (CHM) file viewer for GNOME systems.
 .
 Features are:
  * Support for external ms-its links
  * Full text search support
  * Bookmarks
  * Configurable support for HTTP links
  * Integrated with GNOME2
  * Support for multiple languages
  * Support to open multiple files at once
 .
 Homepage: http://gnochm.sourceforge.net/
Original-Maintainer: Carlos Z.F. Liu <carlosliu@users.sourceforge.net>
```

... But you are right, those few (especially "gconf") could pull a lot more dependencies. So your best bet would probably be to run through an "apt-get --simulate" and see what would happen before it really does happen.
Hi scorp123,


Thanks for your advice.

I solved my problem.  The correct command on running "libchm" is;```

$ extract_chmLib aaa.chm /path/to/directory

```

Previously I made a mistake leaving out "path/to/directory" where aaa.chm to be decompressed.


xchm is great.  With it I can read .chm file directly without decompressing it.


Can you recommend a package to convert .pdf file to .chm?  TIA


B.R.
satimis

---

### Post by MaindotC on 2007-11-14
I apt-get install gnochm and it works perfectly.  Great tool and saves me money on school books...

---

### Post by ugm6hr on 2008-01-06
> **satimis said:**
> 
xchm is great.  With it I can read .chm file directly without decompressing it.


Just found this program.  I think it works just like the Microsoft reader in Windows.  This was one of the few things that annoyingly required me to reboot to Windows to do some projects (e-reading).

The Gutsy repo even has v1.13 (almost the most recent source available).

PS: I heard of it from here: [http://ubuntuforums.org/showpost.php?p=2304235&postcount=53](http://ubuntuforums.org/showpost.php?p=2304235&postcount=53)

EDIT: I have just discovered that you can only copy text (not images) from the .chm file, which is not quite as good as Windows....

EDIT2:
Firefox can open .chm files (but strangely not .CHM - need renaming) with an addon.  The layout is clearer than in xchm.  This also allows selection and saving of images:
[https://addons.mozilla.org/en-US/firefox/addon/3235](https://addons.mozilla.org/en-US/firefox/addon/3235)

---

### Post by olejorgen on 2008-01-06
**archmage** extracts the html files from the .chm file.

---

