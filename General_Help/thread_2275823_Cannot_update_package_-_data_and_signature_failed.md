---
title: "Cannot update package - data and signature failed"
date: 2015-04-28
forum: General Help
---

### Post by BeniaminK on 2015-04-28
When I am trying to update, I get an error:

```
Ign http://switch.dl.sourceforge.net  InRelease                                Splitting up /var/lib/apt/lists/partial/switch.dl.sourceforge.net_project_jedit_InRelease into data and signature failed
E: GPG error: http://switch.dl.sourceforge.net  InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
```

What should I do?

---

### Post by Bashing-om on 2015-04-28
BeniaminK; Well .... 

I also can not resolve that link as provided .. show us your source 'gets' :
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we see what we can finger out.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by BeniaminK on 2015-04-28
These are the inputs from the console:
```
(23:28:47) beniamin: ~ $ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted
     2    # Ubuntu - podstawowe repozytoria
     3    deb http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
     4    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
     5    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse
     6    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse
     7    deb http://security.ubuntu.com/ubuntu trusty-security main restricted universe multiverse
     8    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted universe multiverse
     9    deb http://extras.ubuntu.com/ubuntu trusty main
    10    deb-src http://extras.ubuntu.com/ubuntu trusty main
    11    
    12    # Ubuntu Partner
    13    deb http://archive.canonical.com/ubuntu trusty partner
    14    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    15    deb-src http://archive.canonical.com/ubuntu trusty partner
    16    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty universe multiverse main restricted
    17    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    18    deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse
    19    
    20    ## This software is not part of Ubuntu, but is offered by third-party
    21    ## developers who want to ship their latest software.
    22    deb http://switch.dl.sourceforge.net/project/jedit /
    23    deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
    24    # deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
(23:30:40) beniamin: ~ $ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/dropbox.list <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu trusty main

==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu trusty main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/mc3man-trusty-media-trusty.list <==
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main

==> /etc/apt/sources.list.d/mc3man-trusty-media-trusty.list.save <==
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main

==> /etc/apt/sources.list.d/me-davidsansome-clementine-trusty.list <==
deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main
# deb-src http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main
# deb-src http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main

==> /etc/apt/sources.list.d/me-davidsansome-clementine-trusty.list.save <==
deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main
# deb-src http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main
# deb-src http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main

==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/steam.list.save <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/thomas_tsai-ubuntu-tuxboot-trusty.list <==
deb http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu trusty main

==> /etc/apt/sources.list.d/thomas_tsai-ubuntu-tuxboot-trusty.list.save <==
deb http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu trusty main
```

The problem seems to be in file sources.list in line:

```
deb http://switch.dl.sourceforge.net/project/jedit /
```

---

### Post by Bashing-om on 2015-04-28
BeniaminK; Yeah ..

agreed .. I am still not able to get the link to resolve, Maybe but a temporary problem with sourceforge, but I can not say.
I have no prior experience with sourceforge's site .

What you can do for now is disable that source, update/upgrade the system and check with sourceforge on that status of that link.

Just cause it is tacked on
[INDENT][INDENT][INDENT]does not mean it is a part of 'buntu
[/INDENT][/INDENT][/INDENT]

---

