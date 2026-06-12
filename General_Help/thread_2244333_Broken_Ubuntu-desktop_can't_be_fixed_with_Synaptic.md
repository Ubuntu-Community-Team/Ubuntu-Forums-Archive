---
title: "Broken Ubuntu-desktop can't be fixed with Synaptic?"
date: 2014-09-15
forum: General Help
---

### Post by hoodnun on 2014-09-15
Okay so I'm trying to free up some space on my laptop so I can upgrade to a newer version of Ubuntu, I was trying to delete some programs when it yelled at me about how I have a broken package. I opened up Synaptic and it turned out to be ubuntu-desktop, it told me it was going to download something called "libatk-adaptor-schemas" I tried to fix the broken package and I got this instead:
[B]E: /var/cache/apt/archives/libatk-adaptor-schemas_2.4.0-1ubuntu2_i386.deb: trying to overwrite '/usr/share/glib-2.0/schemas/org.a11y.atspi.gschema.xml', which is also in package libatk-adaptor 2.2.1-0ubuntu1

[/B]It's apparently refusing to fix this broken package. How in the hell do I do this now?
Should I just totally delete and reinstall ubuntu-desktop? I'm not good with terminal commands so I need some help lol. 
Thanks!

---

### Post by grahammechanical on 2014-09-15
If you delete ubuntu-desktop do not reboot until you have re-installed or you wlll most definitely have a broken desktop. If you do not have an alternative UI installed then never allow ubuntu-desktop to be removed.

Synaptic has a feature where we can mark a package for re-installation. It might be safe to use that feature.

Regards.

---

### Post by hoodnun on 2014-09-15
I tried to just mark ubuntu-desktop for reinstallation and do that but I got the same message again. I don't even know how the hell this dumb thing got broken. It's so frustrating I just wanted to free up some space and now all this.

---

### Post by hoodnun on 2014-09-15
Just tried sudo apt-get  -f install and got this, as I have been with everything else I've tried.

**Reading package lists... Done**
**Building dependency tree       **
**Reading state information... Done**
**Correcting dependencies... Done**
**The following extra packages will be installed:**
**  libatk-adaptor-schemas**
**The following NEW packages will be installed:**
**  libatk-adaptor-schemas**
**0 upgraded, 1 newly installed, 0 to remove and 1522 not upgraded.**
**1 not fully installed or removed.**
**Need to get 2,106 B of archives.**
**After this operation, 41.0 kB of additional disk space will be used.**
**Do you want to continue [Y/n]? y**
**Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libatk-adaptor-schemas i386 2.4.0-1ubuntu2 [2,106 B]**
**Fetched 2,106 B in 5s (403 B/s)                   **
**(Reading database ... 163416 files and directories currently installed.)**
**Unpacking libatk-adaptor-schemas (from .../libatk-adaptor-schemas_2.4.0-1ubuntu2_i386.deb) ...**
**dpkg: error processing /var/cache/apt/archives/libatk-adaptor-schemas_2.4.0-1ubuntu2_i386.deb (--unpack):**
** trying to overwrite '/usr/share/glib-2.0/schemas/org.a11y.atspi.gschema.xml', which is also in package libatk-adaptor 2.2.1-0ubuntu1**
**No apport report written because MaxReports is reached already**
**                                                              Processing triggers for libglib2.0-0 ...**
**Errors were encountered while processing:**
** /var/cache/apt/archives/libatk-adaptor-schemas_2.4.0-1ubuntu2_i386.deb**
**E: Sub-process /usr/bin/dpkg returned an error code (1)**

---

### Post by hoodnun on 2014-09-15
There appears to be a similar problem with libatk-adaptor-schemas [https://bugs.launchpad.net/ubuntu/+source/at-spi2-atk/+bug/981140](https://bugs.launchpad.net/ubuntu/+source/at-spi2-atk/+bug/981140)
What happens if I do "[COLOR=#333333][FONT=monospace]sudo dpkg --remove libatk*" and what is this package even used for?[/FONT][/COLOR]

---

### Post by hoodnun on 2014-09-15
Also, if I do 
sudo apt-get install &#8211;reinstall ubuntu-desktop
sudo apt-get build-dep ubuntu-desktop
will I be okay? I feel like uninstalling and reinstalling it may be my only option but idk

---

### Post by Bashing-om on 2014-09-15
hoodnun; Hello;

What release are you running ?
In 14.04 I show:
> 
sysop@1404mini:~$ apt-cache show libatk-adaptor
Package: libatk-adaptor
Priority: optional
Section: misc
Installed-Size: 79
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Accessibility Team <debian-accessibility@lists.debian.org>
Architecture: amd64
Source: at-spi2-atk
Version: [color=green]2.10.2-2ubuntu1[/color]
Replaces: at-spi


Too early to call, but I bet you are running a PPA version; I would suggest you 'ppa-purge' if that is the case.
Let's look:
```

apt-cache policy libatk-adaptor

```

As to it's use; see:
```

apt-cache show libatk-adaptor

```
I can not advise if you require it on your system, it is installed for a reason - but it is not installed on my system.

One thing at a time ->
[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mc4man on 2014-09-15
you could remove libatk-adaptor, update your sources then re-install if the precise version is available (2.4.0-1ubuntu2 
Currently you have the oneiric version installed which is the source of this issue (2.2.1-0ubuntu1

As far as ubuntu-desktop, it would be good to have installed if trying to upgrade from 12.04 to 14.04. If you are trying to upgrade 11.10 to 12.04 **&** you need 11.10 fully updated then that train has left the station. You'd need to add the old-release repo for oneiric, update , ect.

As far as rebooting/logging out with the ubuntu-desktop package removed  - doesn't matter. It's just a metapackage. (I almost never have it installed here as it deps on stuff I remove..

---

### Post by ian-weisser on 2014-09-15
> **hoodnun said:**
> E: /var/cache/apt/archives/**libatk-adaptor-schemas_2.4.0-1ubuntu2**_i386.deb: trying to overwrite '/usr/share/glib-2.0/schemas/org.a11y.atspi.gschema.xml', which is also in package **libatk-adaptor 2.2.1-0ubuntu1**

You have two packages:

libatk-adaptor 2.2.1-0ubuntu1 (already installed)
libatk-adaptor-schemas 2.4.0-1ubuntu2 (trying to install)

They conflict. You cannot have both installed at the same time. Ever.
You must decide which one you really want installed.

---

