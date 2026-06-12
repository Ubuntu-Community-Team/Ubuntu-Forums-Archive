---
title: "apt-get wants to remove ubuntu-desktop [Resolved]"
date: 2007-02-18
forum: General Help
---

### Post by altaaa on 2007-02-18
Okay, here's the deal.

When I use apt-get I always use the -s flag to check apt-get's output. With several programs, when I try to remove them, apt-get wants to remove the ubuntu-desktop package as well. For example:

```
[FONT="Courier New"]ruurd@ruurd-laptop:~$ aptitude search totem
p   libtotem-plparser-dev                          - Totem Playlist Parser library - development version      
i   libtotem-plparser1                             - Totem Playlist Parser library - runtime version          
p   libtotem-plparser1-dbg                         - Totem Playlist Parser library - debugging version        
i   totem                                          - A simple media player for the Gnome desktop (dummy packag
c   totem-gstreamer                                - A simple media player for the Gnome desktop based on gstr
v   totem-gstreamer-firefox-plugin                 -                                                          
i   totem-mozilla                                  - Totem Mozilla plugin                                     
i   totem-xine                                     - A simple media player for the Gnome desktop based on xine
v   totem-xine-firefox-plugin                      -                                                          
ruurd@ruurd-laptop:~$ sudo apt-get remove totem-xine -s
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ubuntu-desktop totem-xine totem totem-mozilla
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  totem totem-mozilla totem-xine ubuntu-desktop
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Remv ubuntu-desktop [1.30]
Remv totem [2.16.2-0ubuntu3]
Remv totem-mozilla [2.16.2-0ubuntu3]
Remv totem-xine [2.16.2-0ubuntu3]
ruurd@ruurd-laptop:~$ [/FONT]
```

Wouldn't removing ubuntu-desktop be a bad thing?

---

### Post by aysiu on 2007-02-18
That's weird. *totem-xine* isn't one of the default packages.

Removing *ubuntu-desktop* isn't immediately harmful, but keeping it can make your transition to Feisty (in two months) easier.

I don't know why *apt-get* wants to remove *ubuntu-desktop*.

What does the -s flag do exactly?

---

### Post by altaaa on 2007-02-18
> **aysiu said:**
> That's weird. *totem-xine* isn't one of the default packages.

Removing *ubuntu-desktop* isn't immediately harmful, but keeping it can make your transition to Feisty (in two months) easier.

I don't know why *apt-get* wants to remove *ubuntu-desktop*.

What does the -s flag do exactly?

It simulates the actions done by apt-get.

---

### Post by mcduck on 2007-02-18
> **aysiu said:**
> That's weird. *totem-xine* isn't one of the default packages.

Removing *ubuntu-desktop* isn't immediately harmful, but keeping it can make your transition to Feisty (in two months) easier.

I don't know why *apt-get* wants to remove *ubuntu-desktop*.

What does the -s flag do exactly?

I've noticed that ubuntu-desktop needs totem, either totem-xine ot totem-gstreamer works. And that's why removing totem-xine removes ubuntu-desktop.

Not that it really matters as ubuntu-desktop is only needed for dist-upgrading to new Ubuntu versions..

(-s flag is 'simulate', meaning that it tells you what it would do without ctually doing any changes to your system.)

---

### Post by altaaa on 2007-02-18
But isn't ubuntu-desktop the Gnome desktop? Just as there are the kubuntu-desktop, xubuntu-desktop and edubuntu-desktop packages? I wouldn't want to remove Gnome from my system.

---

### Post by mcduck on 2007-02-18
No, ubuntu-desktop (just like kubuntu-desktop and others) is a metapackage, meaning that it doesn't contain anything but depends on many other packages. (but not other package depends on it). So installing ubuntu-desktop will install Gnome and all apps that are in the default Ubuntu desktop, but removing the ubuntu-desktop package will not remove anything else than the metapackage.

Metapackages are often used to install groups of packages in easy way.

---

### Post by altaaa on 2007-02-18
> **mcduck said:**
> No, ubuntu-desktop (just like kubuntu-desktop and others) is a metapackage, meaning that it doesn't contain anything but depends on many other packages. (but not other package depends on it). So installing ubuntu-desktop will install Gnome and all apps that are in the default Ubuntu desktop, but removing the ubuntu-desktop package will not remove anything else than the metapackage.

Metapackages are often used to install groups of packages in easy way.

Okay, thanks for the explanation! I guess it's safe to remove then, since I'm not planning to dist-upgrade to Feisty anyway. I prefer clean installs :)

---

### Post by g8m on 2007-02-18
I noticed the same with totem. A while back totem changed from xine to gstreamer. Dont know why. But after that I could'n play dvd's anymore so I wanted to go back to totem-xine. And I didnt because apt told me it was gona uninstall gnome-desktop. Scared the hell out of me. So I installed vlc to play dvd's.

I noticed that totem-gstreamer can play dvd's but only when you play it from the automount prompt. Dont know why.

---

