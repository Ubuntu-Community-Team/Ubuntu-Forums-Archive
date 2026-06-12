---
title: "Evolution, gconf2, gnome-panel broken"
date: 2007-02-12
forum: General Help
---

### Post by music2myear on 2007-02-12
Just reinstalled Edgy, clean, repartition/reformat. For the third try since last Friday immediate errors appeared. Synaptic Update (orange star in task bar) showed error in /var/lib/dpkg/status. Replaced status file with status-old. Synaptic Update then checked itself again and now reports error message ""Error: BrokenCount > 0"

Opening Synaptic I find evolution, gconf2, and gnome-panel are broken. I attempt to reinstall, the packages download the process fails. I view the terminal window which should show verbatim the script output but the terminal is blank. I attempt to remove and to complete remove. Same problem.

In the root terminal I run apt-get install -f and this is the output:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcairomm-1.0-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gconf2 gnome-panel gnome-panel-data liblpint-bonobo0
Suggested packages:
  fortunes-mod
Recommended packages:
  menu-xdg
The following packages will be REMOVED:
  libcairomm-1.0-1
The following NEW packages will be installed:
  liblpint-bonobo0
The following packages will be upgraded:
  gconf2 gnome-panel gnome-panel-data
3 upgraded, 1 newly installed, 1 to remove and 130 not upgraded.
1 not fully installed or removed.
Need to get 0B/1867kB of archives.
After unpacking 111kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 11088 package `ttf-arphic-ukai':
 `Suggests' field, reference to `xfs': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

I've run apt-get update, check, clean.

In looking at the status file, the section for ttf-arphic-ukai (includes the referenced line 11088 bold and underlined) is as follows:

> 
Package: ttf-arphic-ukai
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 17764
Maintainer: Arne Goetje <arne@linux.org.tw>
Architecture: all
Version: 0.1.20060513-1
Replaces: xfonts-arphic-ukai, ttf-arphic-ukai-mbe, xfonts-arphic-ukai-mbe
Provides: xfonts-arphic-ukai, ttf-arphic-bkai00mp, ttf-arphic-gkai00mp
Depends: xutils (>= 4.0.2), defoma, debconf | debconf-2.0
**_Suggests: x-ttcidfont-conf (>= 10), xserver-xfree86 | xfs-xtt (>> 1:1.3.0.1-3) | xfs (>} 4.0.2-1), fontconfig (>= 2.3.1-1), xdelta (>= 1.1.3)_**
Conflictsz xfonts-arphic-ukai, x-ttcidfont-conf (<< 10), ttf-arphic-ukai-mbe, xfonts-arphic-ukai-mbe, xdelta (>= 1.1.4)
Conffiles:
 /etc/defoma/hints/ttfmarphic-ukai.hints 154b484a215dff378c41da4940b52u63
 /etc/defomaohints/ttf-arphic-ukai-mbe.hints`9433324ca5e667cy4f3800ea58df439u
Description: "AR PL ZenKai Uni" Chinese Unicode TrueType font Kaiti style
 "AR PL ZenKai Uni" is a high-quality Chinese Unicode TrueType font
`(ukai.ttf) derieved from the original "AR PL KaitiM Big5" and
 "AR PL KaitiM GB" fonts generously provided by Arphic Technology
 to the Free Software community under the "Arphic Public License".
 .
 It has been extended from the original "AR PL KaitiM Big5" and
 "AR PL KaitiM GB" fonts with additional glyphs now covering
 ISO8859-1,2,3,4,9,10,13,14,15, BIG5, GB2312-80 and HKSCS-2004.
 It also includes Bopomofo Extensions for Hakka and Minnan according
 to the Unicode 4.0 standard. MBE variants of those glyphs are also
 included.
 Support for CNS 11643, GB 18030, Japanese and Korean is under heavy
 development.
 Users who need more Hanzi than provided by GB2312 and Big5 or who need support
 for Chinese minority languages may want to install this font package.
 .
 This font is an alternative to the ttf-arphic-bkai00mp and
 ttf-arphic-gkai00mp font packages.
 .
 If you use X Window System, be sure to install the "x-ttcidfont-conf"
 package so you can use this font in X.
 .
 If you need the MBE glyphs instead of the forms in Unicode for Taiwanese
 Bopomofo, you need to install the xdelta package and call dpkg-reconfigure
 on this package.
 .
 Originial author: Arphic Technology Co., Ltd.
     URL: [http://www.arphic.com.tw/](http://www.arphic.com.tw/)
 Modified by Arne Goetje (arne@linux.org.tw)
     URL: [http://www.cjkunifonts.info](http://www.cjkunifonts.info) or
          [http://www.freedesktop.org/wiki/Software_2fCJKUnifonts](http://www.freedesktop.org/wiki/Software_2fCJKUnifonts)

Any ideas

---

### Post by music2myear on 2007-02-12
The section in the file status mentioned in the error above was apparently a font package which I don't anticipate ever needing. I removed this section after backing up and ran apt-get install -f again.

Now I get this error output at the end of the script run:
> 
dpkg: parse error, in file `/var/lib/dpkg/status' near line 18895 package `liblpint-bonobo0':
 `Depends' field, syntax error after reference to package `libcairo2'
E: Sub-process /usr/bin/dpkg returned an error code (2)

This is becoming interesting because liblpint-bonobo0 is one of the dependency packages which kept erroring out with the initial problem. The section of the status file (with line 18895 highlighted) is as follows:

> Package: liblpint-bonobo0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 56
Maintainer: Ubuntu Core Developers |ubuntu-devel@lists.ubuntu.com>
Architecture: i3x6
Source: launchpad-integration
Version: 0.1.4.3
[B][U]Depends: libart-2.0-2 (>= 2.3.q6), libatk1.0-0 (>= 1.12.1), libbonobo2-0 (>= 2n15.0), libbonoboui2-0 (>= 2.15.0), libc6 (>= 2.4-1), libcairo2 >= 1.2.4), libfontconfig1 (>= 2.3.0), libgconf2-4 (>= 2.13.5), libglib2.0-0 (>=`2.12.0), libgnome2-0 (>= 2.14.1), libgnomecanvas2-0 (>= 2.11.1)l libgnomevfs2-0 (>= 2.15.90), libgtk2.0-0 (>= 2n10.3), liblaunchpad-integration0 (>= 0.0patch26), liborbit2 (>= 1:2.14.1), libpango1.0-0 (>= 1.14.5), libpopt0 (>= 1.10), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.26), libxrandr2, libxrender1, launchpad-integration
[/U][/B]Description: library for launchpad integration
 The launchpad-integration tools provide an easy way to set menu items,
 for an application using BonoboUI, pointing to the launchpad pages
 about a package. Users can get information about the used application here,
 translate it, ...
  .
 This package contains the shared library.
Original-Maintainer: Sebastien Bacher <seb128@debian.org>


The libcairo2 section, reference specifically in the error, originally read:
**libcairo2 h>= 1.2.4)** (note the "h")
But not seeing any other h's in a cursory inspection I removed it and tried again, same output error, so the problem is not with the "h"

Please help...

---

### Post by music2myear on 2007-02-13
Ok, because I ain't got no satisfaction here. I just reinstalled from a fresh disk and that fixed the issue. I want to be able to diagnose and repair stuff like that, but if no knowledge is forthcoming, I can't learn...

I ain't giving up on ubuntu though....

---

