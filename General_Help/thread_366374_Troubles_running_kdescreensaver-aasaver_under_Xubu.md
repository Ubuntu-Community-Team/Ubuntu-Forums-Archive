---
title: "Troubles running kdescreensaver-aasaver under Xubuntu"
date: 2007-02-20
forum: General Help
---

### Post by hilltop_yodeler on 2007-02-20
I've seen the ASCIIaquarium screensaver run under KDE and I think that it looks pretty slick.  I would like to run it under Xubuntu Edgy Eft.  Since I am running other KDE apps under XFCE, I am assuming that the ASCIIscreensaver will also run with Xubuntu, but perhaps that is an incorrect assumption.

I downloaded the .deb package for i386 from [http://packages.ubuntulinux.org/edgy/kde/kdescreensaver-aasaver](http://packages.ubuntulinux.org/edgy/kde/kdescreensaver-aasaver)
and used the GDebi Package Installer to install the package.  I guess that kdescreensaver-aasaver is the screensaver version of ASCIIquarium, which is a Perl application. The details for the included files (through GDebi) reads as follows:
./
usr/
usr/bin/
usr/bin/asciiquarium.kss
usr/share/
usr/share/applnk/
usr/share/applnk/System/
usr/share/applnk/System/ScreenSavers/
usr/share/applnk/System/ScreenSavers/asciiquarium.desktop
usr/share/config.kcfg/
usr/share/config.kcfg/asciiquarium.kcfg
usr/share/doc/
usr/share/doc/kdescreensaver-aasaver/
usr/share/doc/kdescreensaver-aasaver/copyright
usr/share/doc/kdescreensaver-aasaver/changelog.Debian.gz

When I run find for kdescreensaver-aasaver, the only location that I can find for it is:
/usr/share/doc/kdescreensaver-aasaver
Running ls -la, I see the following:
total 52
drwxr-xr-x    2 root root  4096 2007-02-20 17:16 .
drwxr-xr-x 1031 root root 28672 2007-02-20 16:27 ..
-rw-r--r--    1 root root   333 2006-02-22 08:40 changelog.Debian
-rw-r--r--    1 root root   232 2006-02-22 08:40 changelog.Debian.gz
-rw-r--r--    1 root root   547 2006-02-22 08:40 copyright

The screensaver does not show up in my XScreenSaver Preferences.  

I also tried installing the tar.gz file from [http://www.robobunny.com/projects/asciiquarium/](http://www.robobunny.com/projects/asciiquarium/).  This is the actual ASCIIaquarium, written in Perl; I was able to make the app run, but not as a screensaver -- only as a stand-alone application.  I don't see a way to import it as a screensaver.

Anyone have any ideas?

Thanks!

- Darrin

---

