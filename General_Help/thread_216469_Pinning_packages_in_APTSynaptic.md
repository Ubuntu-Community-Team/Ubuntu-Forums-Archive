---
title: "Pinning packages in APT/Synaptic"
date: 2006-07-15
forum: General Help
---

### Post by matthias_k on 2006-07-15
Hi,

I want to prevent Ubuntu from upgrading certain packages with versions from the Seveas repository, so I defined the following lines in /etc/apt/preferences:

```

Package: acroread
Pin: release a=dapper-seveas
Pin-Priority: -1

Package: mozilla-acroread
Pin: release a=dapper-seveas
Pin-Priority: -1

```
However, both APT and Synaptic ignore the pins, both still want to upgrade to the new version in the Seveas repo. How come?

---

### Post by matthias_k on 2006-07-15
This is driving me nuts. If I define a negative pin, that is, a pin which defines which packages should be ignored for updates by supplying a negative priority, it doesn't work.

If however I explicitly define which packages /are/ allowed to be installed/upgraded, it works... But this is not what I want, e.g. I don't want gnome-main-menu to be installed from the official archives.

---

### Post by matthias_k on 2006-07-17
Not solved :-)

---

### Post by Rui Pais on 2006-07-17
hi,
it seems that dapper ignores that way to pinn packages (or at least, if i remember well, UbuntuWiki says something of the kind)

Try to do it with synaptic. 
Under the 'Package' entry of the menus there is a lock option. 
I think it pinns versions to both synaptic and apt. 
If apt still don't see it as pinned, try to install wajig, and run
wajig hold <app> and to reverse, wajig unhold <app>

hope that helps

---

### Post by Jagot on 2006-07-17
In Synaptic, if you click on whatever the package is then go up to one of the menus (I think it's 'Package' - not on my Ubuntu box at the moment so can't say for sure).  There should be the option to lock the package.

Alternatively, in terminal issue this command:

```
sudo aptitude hold packagename
```

---

### Post by matthias_k on 2006-07-18
Yes I know, but that's not what I want. If I lock a package in synaptic, it will never be updated again until I unlock it. What I want is to *prioritize* a version in repository A over a version in repository B, but of course I still want it to receive updates.

In other words, what I need is a "fetch package X from repo Y" setting, and that's what /etc/apt/preferences does. Since Synaptic is only a fancy frontend to apt, I was confident that this would work. :-/

---

### Post by aysiu on 2006-07-18
This isn't on a per-package basis, but have you tried going to Settings > Preferences > Distribution > Prefer Version from...?

---

### Post by matthias_k on 2006-07-18
I need it on a per-package basis, unfortunately.

---

### Post by aysiu on 2006-07-18
Maybe it's a syntax issue? > Using Non-Debian Sources

If you're using non-Debian sources, you've got the same problem, only more so because there's no natural ordering as there is with Debian's stable -> testing -> unstable. Without explicitly listing them in /etc/apt/preferences, they're all at priority 500, so a package installed from one source can be replaced by a higher version supplied by a different source.

A partial fix for this is to pin each source at a different priority. Eg,

Package: *
Pin: origin [www.debian-multimedia.org](www.debian-multimedia.org)
Pin-Priority: 600

Package: *
Pin: origin [www.ibiblio.org](www.ibiblio.org)
Pin-Priority: 610

Package: *
Pin: origin [www.argon.org](www.argon.org)
Pin-Priority: 620

These settings would mean that a package installed from [www.argon.org](www.argon.org) wouldn't automatically be replaced with one from the other two, and one from [www.ibiblio.org](www.ibiblio.org) wouldn't be replaced with one from [www.debian-multimedia.org](www.debian-multimedia.org).

Working in the other direction the packages would still be replaced, however: If you've installed a package from [www.ibiblio.org](www.ibiblio.org) and a newer version becomes available from [www.argon.org](www.argon.org), apt-get will upgrade to it. The only way I know of to prevent that is to explicitly pin the package to the source via /etc/apt/preferences. 

---

