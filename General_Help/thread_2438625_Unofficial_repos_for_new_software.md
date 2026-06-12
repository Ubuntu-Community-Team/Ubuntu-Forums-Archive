---
title: "Unofficial repos for new software?"
date: 2020-03-15
forum: General Help
---

### Post by u666sa on 2020-03-15
Guys. Ubuntu has anchient software. Is there at least a 3rd party repo for new stuff??

---

### Post by CelticWarrior on 2020-03-15
Yes, there are PPAs that offer some newer versions. What do you need specifically?

---

### Post by u666sa on 2020-03-15
Specifically I’m from fedora 31 and I want new stuff in video, multimedia, utilities etc. So that I don’t have to compile from source here.

I want rpmfusion
Negativo
Cheese

Something like that.

Latest man!

---

### Post by Impavidus on 2020-03-15
In Ubuntu, the versions of most software get frozen a few weeks before that Ubuntu is released. After that, you only get bugfixes. So, in Ubuntu 18.04 you now have two year old software. Ubuntu 19.10 has software from about half a year ago.

There are third party repos, called PPAs. Use at your own risk, as these are often the cause of instability. If you really wish the latest releases of all software, consider a rolling release distro.

---

### Post by CelticWarrior on 2020-03-15
> **u666sa said:**
> Specifically I’m from fedora 31 and I want new stuff in video, multimedia, utilities etc. So that I don’t have to compile from source here.

So you don't have any specific problem to solve? It seems all you want is newer versions just because...

> I want rpmfusion
Negativo
Cheese

Something like that.


You don't need any newer version unless you want to solve a specific problem or looking for a new functionality. The latest isn't always the greatest.

The software included in any Ubuntu release has been tested to work with that release while newer non-tested version may break something. That IS how any non-rolling release works, BTW. Using a stable non-rolling release like Ubuntu and then complaining about the software versions is quite stupid IMHO. Users who want the latest should go for a rolling release.

Now...
*rpmfusion*  isn't for Ubuntu. Ubuntu, like Debian, uses DEB. Some software packaged as RPM can be installed, often with caveats, by using *alien*.

*Negativo* (???) Don't know what this is...

 *Cheese *is at v. 3.34 in Ubuntu 19.10 (don't know what version will come up in 20.04 in April); Latest Fedora has the exact same version. Is there a newer version? NO, THERE ISN'T. 3.34 is also the one you can install from source. This is getting ridiculous by the line...

---

### Post by dragonfly41 on 2020-03-15
[https://www.fosslinux.com/34337/top-20-must-have-apps-for-your-ubuntu-pc.htm](https://www.fosslinux.com/34337/top-20-must-have-apps-for-your-ubuntu-pc.htm)

Stacer is a useful tool.

---

### Post by u666sa on 2020-03-15
> **Impavidus said:**
> In Ubuntu, the versions of most software get frozen a few weeks before that Ubuntu is released.

That is a load of balogna and I can prove it.

[URL="https://imgur.com/KWDsad7.png"]
  [IMG]https://imgur.com/KWDsad7.png[/IMG][/URL]


Latest version of qalculate vailble on Ubuntu 18.04 LTS if 0.9.9...

According to official qalculate history, version 0.9.9 was release on July 26, 2016, [https://qalculate.github.io/news.html](https://qalculate.github.io/news.html)


Today is March 15 2020. Ubuntu 18.04 was released on [FONT=sans-serif]26 April 2018. January 2018 version 2 of qalculate was already availble.


Now the truth.  Ubuntu is based on Debian, and they don't bother compiling new software, citing stability.  Cononical are the creators of snap, a stop gap measure to combat its old software problem, nothing more.  Thus the problem.  Debian based distoros have anchient software, not because of stability issues, but because it's hard to compile new stuff all the time.

On the other hand is Fedora with it's latest stuff.  Problem with Fedora is not it's latest software, but, for me at least, latest Linux kernel, which does not work with 390 drivers. It is NVIDIA problem really, because NVIDIA does not support its old products on Linux, they are just like Apple in a way. 


It's obvious, Ubuntu has anchient software.  It is a problem.  Would you use qalculate 0.9.9 when version 3.8 is available?  I think not, cuz they don't even look the same.


Case closed, you are wrong about 2 year close gap theory.  They just use old software so that they don't have to compile new software, they are lazy. [/FONT]

---

### Post by Dennis N on 2020-03-15
> Specifically I’m from fedora 31 and I want new stuff in video, multimedia, utilities etc. So that I don’t have to compile from source here.

Some of the common applications like LibreOffice, Gimp, Inkscape, Krita, Kate, Audacity, Kdenlive, Firefox, Cheese and many more have Flatpak and/or Snap versions. I use several of these Flatpak and Snap applications on Ubuntu 18.04 to have the up-to-date versions. I tend to favor the Flatpak if available, and have had no problems with them.

My own Flatpaks:
```
dmn@Tyana:~$ flatpak list --app
Name                                Application ID                       Version        Branch     Installation
Marker                              com.github.fabiocolacio.marker       2019.11.06     stable     system
ghostwriter                         io.github.wereturtle.ghostwriter     1.8.0          stable     system
Scribus                             net.scribus.Scribus                  1.5.5          stable     system
Extreme Tuxracer                    net.sourceforge.ExtremeTuxRacer                     stable     system
SuperTuxKart                        net.supertuxkart.SuperTuxKart        1.1            stable     system
Bluefish                            nl.openoffice.bluefish               2.2.10         stable     system
Frozen Bubble                       org.frozen_bubble.frozen-bubble      2.213          stable     system
Geany                               org.geany.Geany                      1.36           stable     system
GNU Image Manipulation Program      org.gimp.GIMP                        2.10.18        stable     system
GNOME Maps                          org.gnome.Maps                       3.34.3         stable     system
Quadrapassel                        org.gnome.Quadrapassel               3.35.92        stable     system
Meld                                org.gnome.meld                       3.20.2         stable     system
Inkscape                            org.inkscape.Inkscape                0.92.4         stable     system
KBlocks                             org.kde.kblocks                      19.12.3        stable     system
Krita                               org.kde.krita                        4.2.8.0        stable     system
LibreOffice                         org.libreoffice.LibreOffice          6.4.1.2        stable     system
Stellarium                          org.stellarium.Stellarium            0.19.1         stable     system

```

And Snaps:
```
dmn@Tyana:~$ snap list
Name                  Version                     Rev   Tracking  Publisher   Notes
atari800-jz           3.1.0-0                     1     stable    jz          -
chromium              80.0.3987.132               1043  stable    canonical&#10003;  -
core                  16-2.43.3                   8689  stable    canonical&#10003;  core
core18                20200124                    1668  stable    canonical&#10003;  base
firefox               74.0-3                      330   stable    mozilla&#10003;    -
gnome-3-28-1804       3.28.0-16-g27c9498.27c9498  116   stable/…  canonical&#10003;  -
gnome-calculator      3.34.1+git1.d34dc842        544   stable/…  canonical&#10003;  -
gnome-characters      v3.32.1+git3.b9120df        399   stable/…  canonical&#10003;  -
gnome-logs            3.34.0                      81    stable/…  canonical&#10003;  -
gnome-system-monitor  3.32.1-3-g0ea89b4922        127   stable/…  canonical&#10003;  -
gtk-common-themes     0.1-28-g1503258             1440  stable/…  canonical&#10003;  -
snap-store            20191114.a9948d5            209   stable    canonical&#10003;  -

```

---

### Post by Frogs Hair on 2020-03-15
Qulculate is not even in the 20.04 repo yet most likely because it is maintained by a 3rd party that is responsible for what if any version they push to the repository. There is a snap. 

```
sudo apt list qulculate
[sudo] password for david: 
Listing... Done

```

```
snap find qalculate
Name          Version  Publisher  Notes  Summary
qalculate     3.8.0    h-k        -      The ultimate desktop calculator
qalculate-jz  1.0.0-2  jz         -      The ultimate desktop calculator
cantor        19.08.0  kde<font color="#4E9A06">&#10003;</font>       -      KDE Frontend to Mathematical Software


```

---

### Post by Dennis N on 2020-03-15
> Latest version of qalculate vailble on Ubuntu 18.04 LTS if 0.9.9...
Qalculate 3.8 is available as a Snap application. So if you want that in Ubuntu 18.04, you can have it.

---

### Post by oldrocker99 on 2020-03-15
Having moved to the easiest way to install Arch, EndeavourOS, which allows your choice of desktop during installation, and gets you into pure Arch, with the largest library of software available, period. And, once it's installed, it's easy to use. The biggest difference between Debian systems (like Ubuntu), Red Hat systems (Fedora, Open SuSe), and Arch (Manjaro, EndeavourOS) is the commands used to install software, apt for Debian, yum for Red Hat, and pacman (supplanted recently by yay) for Arch.

Besides that, with possible rearrangement of system folders, those are, truly, the biggest difference between families of Linux (GNU/Linux, actually). Beyond that, they all run the same software and behave the same way.

And keep asking questions!

---

### Post by QIII on 2020-03-15
> **u666sa said:**
> That is a load of balogna and I can prove it ...

You have proven nothing beyond your trollish intent.  The user did not say the latest release of software is used.  "Frozen" means that software versions are chosen and locked in several weeks in advance, which is entirely factually correct.

Case closed.  It is, in fact, you who are wrong.

---

