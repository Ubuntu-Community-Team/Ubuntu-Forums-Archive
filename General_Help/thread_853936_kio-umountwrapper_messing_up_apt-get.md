---
title: "kio-umountwrapper messing up apt-get"
date: 2008-07-09
forum: General Help
---

### Post by schauerlich on 2008-07-09
**EDIT: I have fixed the problem on my own and posted a solution below for anyone else who finds this thread.**

I installed kubuntu-desktop and later decided KDE wasn't for me. I knew kubuntu-desktop was just a metapackage and that I wouldn't be able to uninstall it with apt-get remove, so I went over to psychocats and followed this tutorial:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Except I didn't do "&& sudo apt-get install xubuntu-desktop" because I didn't want xfce, I just wanted KDE gone. I came there from a google search and didn't see the "Pure Gnome" section, so that was probably where I messed up... :/ .now every time I try to use apt-get or aptitude, I get an error having to do with kio-umountwrapper. I get a list of the packages it will install, the size of the packages, etc, and then this:

```

Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
(Reading database ... 113573 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

```It doesn't matter what package I try, I get the same error. Does anyone know of a fix, or am I basically going to have to reinstall?

[color=red]Solution:[/color]From: [https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729/comments/4](https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729/comments/4)

```

mkdir -p /usr/share/apps/d3lphin/servicemenus/
 touch /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib

```

---

