---
title: "Hoary Transcode repository?"
date: 2005-06-25
forum: General Help
---

### Post by govert on 2005-06-25
I spent about 6 hours yesterday, trying different reposities, compiling from scratch, etc, but nowhere could I find a way to install transcode without breaking dependencies on Hoary. 

currenty, I beleive that I have installed transcode from Marrilat.
* deb: transcode_0.6.14-0.4_i386.deb
* repository: deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

Result: broken dependencies that I do not know how to resolve.


Is there a Horay repository including transcode or not?
Please help.

---

### Post by Xian on 2005-06-25
[QUOTE=govert]Is there a Horay repository including transcode or not?
Please help.[/QUOTE]
Yes, it is in the backport repos. 
You need to remove those Marrilat links in your /etc/apt/sources.list

```
##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
```

---

### Post by govert on 2005-06-25
[QUOTE=Xian]Yes, it is in the backport repos. 
You need to remove those Marrilat links in your /etc/apt/sources.list

```
##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
```[/QUOTE]


BIG thanks!

The apt-get went fine. Havent tested the binaries, but
I presume all is nice and dandy :-)

Thanks again.

---

### Post by RikBlankestijn on 2005-07-20
Hi, I also tried those sources because I need to get transcode but here is what I get when loading the package manager:
[COLOR=DarkGreen]
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/universe Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/multiverse Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/restricted Packages (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
[/COLOR]
I'm pretty new to ubuntu so I may have done something wrong. I've included the above sources in /etc/apt/sources.list. Can someone please help me?

---

