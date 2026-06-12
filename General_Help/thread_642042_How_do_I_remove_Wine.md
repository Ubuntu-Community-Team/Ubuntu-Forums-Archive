---
title: "How do I remove Wine?"
date: 2007-12-16
forum: General Help
---

### Post by Game_boy on 2007-12-16
Note: The "similar threads" did not help me.

 I installed Wine 0.9.50 from source with ./tools/wineinstall

I deleted the making files irretrievably.

Some time later, Wine 0.9.51 came out. I installed it from the website as a .deb, but winecfg gives the installed Wine version as 0.9.50 and apt-get reports the installed version as 0.9.51. After apt-get remove --purge wine, apt-get reports no version is installed but winecfg still exists and reports itself as 0.9.50.

I want to return to a .deb based management rather than having to recompile every new release with possible conflicts.

How can I uninstall Wine so that I can do this?

---

### Post by cmnorton on 2007-12-16
You should be able to search for wine in Synaptic package manager, and then select either remove or completely remove.

---

### Post by mc4man on 2007-12-16
You will want to delete your .wine directory, also do a search for wine, there are numerous files left over from a complete removal - maybe one or more is related to your issue. Normally you wouldn't need to delete any except for menu issues on a reinstall

---

### Post by #!/bin/bash on 2007-12-16
Remove these files:
/usr/bin/wmc
/usr/bin/wrc
/usr/bin/regsvr32
/usr/bin/widl
/usr/bin/wine
/usr/bin/wineserver
/usr/bin/winebuild
/usr/bin/winemaker
/usr/bin/regedit
/usr/bin/uninstaller
/usr/bin/wine-pthread
/usr/bin/winebrowser
/usr/bin/wine-kthread
/usr/bin/wineshelllink
/usr/bin/wineconsole
/usr/bin/function_grep.pl
/usr/bin/msiexec
/usr/bin/wineboot
/usr/bin/winedump
/usr/bin/winefile
/usr/bin/winemine
/usr/bin/winepath
/usr/bin/notepad
/usr/bin/winecfg
/usr/bin/winedbg
/usr/bin/winegcc
/usr/bin/winhelp
/usr/bin/wine-preloader
/usr/bin/wineprefixcreate
/usr/bin/winelauncher
/usr/bin/progman
/usr/man/man1/wine.1.gz
/usr/man/man1/wmc.1.gz
/usr/man/man1/winedbg.1.gz
/usr/man/man1/wineprefixcreate.1.gz
/usr/man/man1/wineserver.1.gz
/usr/man/man1/winemaker.1.gz
/usr/man/man1/winebuild.1.gz
/usr/man/man1/widl.1.gz
/usr/man/man1/wrc.1.gz
/usr/man/man1/winedump.1.gz
/usr/man/man1/winegcc.1.gz
/usr/share/aclocal/wine.m4
/usr/share/applications/wine.desktop

Remove these directorys
/usr/doc/wine-0.9.50/
/usr/lib/wine/
/usr/share/wine/
/usr/include/wine/

---

