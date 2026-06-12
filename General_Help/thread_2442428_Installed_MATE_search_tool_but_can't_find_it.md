---
title: "Installed MATE search tool but can't find it"
date: 2020-05-03
forum: General Help
---

### Post by Tom_Carr on 2020-05-03
On my new install of 20.04, I went to the software center center and installed the MATE Search tool.  It installed OK and if I go back to the software center it shows up as being installed.  However it does not show up on the launcher bar,  and I can't find it using the box at the top of the screen (don't know the name of that box).

---

### Post by Dennis N on 2020-05-03
Are you using Ubuntu 20.04? Your tag is Ubuntu. If so, consider that the MATE search tool (designed for MATE Desktop) may not function in Ubuntu with Gnome Desktop.

---

### Post by TheFu on 2020-05-03
Mate Search tool is built-into to Ubuntu-Mate. Worked fairly fast once I figured out the directory and look inside stuff. Sorta like find + egrep {} \;.  I have a fresh (yesterday) Ubuntu-Mate 20.04 install here.

```
$ apt search mate-search-tool
Sorting... Done
Full Text Search... Done
mate-utils/focal,now 1.24.0-1 amd64 [installed]
  MATE desktop utilities

mate-utils-common/focal,focal,now 1.24.0-1 all [installed,automatic]
  MATE desktop utilities (common files)

```
Don't know about dependencies, but APT does:
```
$ apt show mate-utils
Package: mate-utils
Version: 1.24.0-1
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian+Ubuntu MATE Packaging Team <debian-mate@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 888 kB
Depends: libmatedict6 (= 1.24.0-1), mate-desktop-common, mate-utils-common (>= 1.24.0-1), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.29), libcairo2 (>= 1.10.0), libcanberra-gtk3-0 (>= 0.25), libcanberra0 (>= 0.2), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.37.3), libgtk-3-0 (>= 3.21.5), libgtop-2.0-11 (>= 2.22.3), libice6 (>= 1:1.0.0), libmate-panel-applet-4-1 (>= 1.18), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libsm6, libudisks2-0 (>= 2.0.0), libx11-6, libxext6, zlib1g (>= 1:1.1.4)
Homepage: http://www.mate-desktop.org/
**Task: ubuntu-mate-core, ubuntu-mate-desktop**
Download-Size: 218 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: MATE desktop utilities
 This package contains all the tools bundled as MATE utilities:
  - mate-disk-usage-analyzer, a disk usage analyser
  - mate-dictionary, a program which can look up the definition of words
    over the internet (including a panel applet to do the same)
  - **mate-search-tool**, with which one can find files by name or content
  - mate-system-log, a log viewing application
  - mate-screenshot, a tool to take desktop screenshots and save them into
    a file

```

First, I'd check whether a snap or .deb package was installed.  Here, it is a .deb package.

The actual name of the program being run is **mate-search-tool**

---

### Post by Tom_Carr on 2020-05-04
> [COLOR=#000000]Are you using Ubuntu 20.04? Your tag is Ubuntu. If so, consider that the MATE search tool (designed for MATE Desktop) may not function in Ubuntu with Gnome Desktop.[/COLOR]

Yes I am using 20.04 ubuntu.  It worked in Ubuntu 18.04.  The problem may be just that it does not show up as an icon on the launcher bar.  In 18.04 that is the only way I could get to it.  It I tried to launch it from the box on the top of the screen I could not find it.

---

### Post by Tom_Carr on 2020-05-04
Almost everything I do in Ubuntu  is with the GUI.  I don't know much about using the terminal commands, but using what you showed me, I just went into the terminal and entered mate-search-tool and it came up.  That is an ok solution.  Thank you.  A better solution would be if I could put an icon in the launch bar that would bring it up.  Do you know how to do that?


> **TheFu said:**
> Mate Search tool is built-into to Ubuntu-Mate. Worked fairly fast once I figured out the directory and look inside stuff. Sorta like find + egrep {} \;.  I have a fresh (yesterday) Ubuntu-Mate 20.04 install here.

```
$ apt search mate-search-tool
Sorting... Done
Full Text Search... Done
mate-utils/focal,now 1.24.0-1 amd64 [installed]
  MATE desktop utilities

mate-utils-common/focal,focal,now 1.24.0-1 all [installed,automatic]
  MATE desktop utilities (common files)

```
Don't know about dependencies, but APT does:
```
$ apt show mate-utils
Package: mate-utils
Version: 1.24.0-1
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian+Ubuntu MATE Packaging Team <debian-mate@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 888 kB
Depends: libmatedict6 (= 1.24.0-1), mate-desktop-common, mate-utils-common (>= 1.24.0-1), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.29), libcairo2 (>= 1.10.0), libcanberra-gtk3-0 (>= 0.25), libcanberra0 (>= 0.2), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.37.3), libgtk-3-0 (>= 3.21.5), libgtop-2.0-11 (>= 2.22.3), libice6 (>= 1:1.0.0), libmate-panel-applet-4-1 (>= 1.18), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libsm6, libudisks2-0 (>= 2.0.0), libx11-6, libxext6, zlib1g (>= 1:1.1.4)
Homepage: http://www.mate-desktop.org/
**Task: ubuntu-mate-core, ubuntu-mate-desktop**
Download-Size: 218 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: MATE desktop utilities
 This package contains all the tools bundled as MATE utilities:
  - mate-disk-usage-analyzer, a disk usage analyser
  - mate-dictionary, a program which can look up the definition of words
    over the internet (including a panel applet to do the same)
  - **mate-search-tool**, with which one can find files by name or content
  - mate-system-log, a log viewing application
  - mate-screenshot, a tool to take desktop screenshots and save them into
    a file

```

First, I'd check whether a snap or .deb package was installed.  Here, it is a .deb package.

The actual name of the program being run is **mate-search-tool**

---

### Post by bruce549 on 2020-05-04
Try mate-search-tool -h in the terminal.

---

### Post by Holger_Gehrke on 2020-05-04
To make a program visible in the graphical starter there needs to be a .desktop file for it either in /usr/share/applications or in ~/local/share/applications. mate-utils does install a .desktop file for the search tool in /usr/share/applications/mate-search-tool.desktop. There might be a line 'OnlyShowIn=Mate' or 'NotShowIn=<list of DE's>' in there. Opening the file in an editor and changing or removing those lines should fix the problem.

Holger

---

### Post by Tom_Carr on 2020-05-04
Thanks everyone for your help.  I decided the easiest thing was to add a keyboard shortcut ctrl-alt-S that runs mate-search-tool.   I never did get it to show up on the desktop, but decided that wasn't important.  It's actually faster to bring it up with the keyboard shortcut.

---

### Post by ActionParsnip on 2020-05-04
Won't that get overwritten in later updates? I suggest making a copy that DOES show in the other DEs so that it doesn't get clobbered by updates

---

