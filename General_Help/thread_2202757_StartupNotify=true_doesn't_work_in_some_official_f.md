---
title: "StartupNotify=true doesn't work in some official flavors?"
date: 2014-01-30
forum: General Help
---

### Post by vasa1 on 2014-01-30
There's a discussion [starting here]("https://lists.ubuntu.com/archives/lubuntu-users/2014-January/006709.html") on why some systems don't support **StartupNotify=true**. The point being made is that users of older systems would find it comforting to know that something is happening when they double-click an application until the application finally appears on their screens. *Of course, this isn't an issue for people with blindingly snappy hardware.*

I've done a bit of googling on the subject and the only "sure" thing seems to be that Kubuntu (KDE) supports it. But then KDE wouldn't be first pick for older hardware, IMO.

Is the (non)functioning of StartupNotify=true dependent on
cursor theme
window manager
desktop enviroment (excluding the WM)?

I've seen mostly Lubuntu users report the issue but one participant in the linked discussion feels that Xfce users experience the issue as well.

---

### Post by Toz on 2014-01-30
I recall reading that in Xfce, startup notification only works if the startup notification libraries are installed and if the app supports it. Can't find that source right now, but have found some info in the [Xfce FAQ](http://wiki.xfce.org/faq) (see "What is the "use startup notification" option?")

---

### Post by vasa1 on 2014-01-30
> **Toz said:**
> I recall reading that in Xfce, startup notification only works if the startup notification libraries are installed and if the app supports it. Can't find that source right now, but have found some info in the [Xfce FAQ](http://wiki.xfce.org/faq) (see "What is the "use startup notification" option?")
Thanks!

I can't access that site right now but I'll try later.

Meanwhile, here's a thread indicating issues with Openbox: [http://icculus.org/pipermail/openbox/2013-July/008028.html](http://icculus.org/pipermail/openbox/2013-July/008028.html).

The later comments [here]("https://bugs.launchpad.net/unity/+bug/862662") point to the issue possibly persisting in Lubuntu 1_4_.04.

---

### Post by Toz on 2014-01-31
I've got an SSD so it hard to test this - everything starts right away. Audicity startup takes the longest - almost a full second to start, and I don't see a busy cursor (but I'm not sure if it supports startup notifications). Perhaps this is broken. Will need to check on an older computer.

---

### Post by vasa1 on 2014-01-31
> **Toz said:**
> I've got an SSD so it hard to test this - everything starts right away. Audicity startup takes the longest - almost a full second to start, and I don't see a busy cursor (but I'm not sure if it supports startup notifications). Perhaps this is broken. Will need to check on an older computer.
I managed to access [http://wiki.xfce.org/faq](http://wiki.xfce.org/faq) and here's what it has:
> What is the "use startup notification" option?

If you select this option, the window manager will show an hourglass while the program is loading. The startup notification libraries have to be installed. They are probably available with your distribution. This feature is only supported by modern applications (Gtk2.x and Qt3.x based).

Please note that the API is not yet frozen, and therefore Xfce 4 is only guaranteed to work with the startup-notification library version >= 0.5.
**apt-cache search startup notification lib** mentions
```
libstartup-notification0 - library for program launch feedback (shared library)
libstartup-notification0-dev - library for program launch feedback (development headers)
```
and I have the first but not the second and version information for the first is
libstartup-notification0:
  Installed: 0.12-3
  Candidate: 0.12-3

Well, I think this issue would concern Lubuntu rather than Xubuntu or any other flavor because Lubuntu sets out to accommodate older computers as far as possible.

---

### Post by Luis_Rossell on 2014-11-14
If you had xubuntu 14.04 LTS try to install this package it worked for me...

[https://launchpad.net/ubuntu/+source/lightdm-gtk-greeter/1.9.0-0ubuntu1](https://launchpad.net/ubuntu/+source/lightdm-gtk-greeter/1.9.0-0ubuntu1)

---

