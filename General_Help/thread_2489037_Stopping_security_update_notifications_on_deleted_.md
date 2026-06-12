---
title: "Stopping security update notifications on deleted app - ImageMagick"
date: 2023-07-16
forum: General Help
---

### Post by ozark_hillbilly on 2023-07-16
Ubuntu 20.04.6LTS

After removing ImageMagick through Synaptic Package Manager I still receive security update notifications from Software Updater on this deleted app.
Do I need to execute a terminal mode command to stop this permanently?

thanks....

---

### Post by #&amp;thj^% on 2023-07-16
EDIT#4 Ubuntu ships with imagemagick.
Being a core dependency of multiple packages, removing ImageMagick may break your system. So make sure you know what you are doing! 
and I use the terminal for installs and un-installs, but what show with:
```
convert --version

```
EDIT: you see that message because:
```
apt policy imagemagick
imagemagick:
  Installed: 8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1
  Candidate: 8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1
  Version table:
 *** 8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/universe amd64 Packages
       **_ 500 http://security.ubuntu.com/ubuntu lunar-security/universe amd64 Packages_**
        100 /var/lib/dpkg/status
     8:6.9.11.60+dfsg-1.6 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages

```
EDIT:#2
To remove and clean left overs I'll use
```
sudo apt autoremove --purge  imagemagick
```
EDIT#3
This is hard one to get rid of due to, This package was (probably) installed because something else you installed asked for it. This other piece of software depends on it. As long as you have that other piece of software installed, your OS will keep re-installing graphicsmagick-imagemagick-compat or imagemagick.

---

### Post by ozark_hillbilly on 2023-07-16
I did run:

ed@ed-G41MT-S2PT:~$ sudo apt autoremove --purge imagemagick
[sudo] password for ed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'imagemagick' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
ed@ed-G41MT-S2PT:~$ 

also:

ed@ed-G41MT-S2PT:~$ convert --version
Version: ImageMagick 6.9.10-23 Q16 x86_64 20190101 [https://imagemagick.org](https://imagemagick.org)
Copyright: © 1999-2019 ImageMagick Studio LLC
License: [https://imagemagick.org/script/license.php](https://imagemagick.org/script/license.php)
Features: Cipher DPC Modules OpenMP 
Delegates (built-in): bzlib djvu fftw fontconfig freetype jbig jng jpeg lcms lqr ltdl lzma openexr pangocairo png tiff webp wmf x xml zlib
ed@ed-G41MT-S2PT:~$

---

### Post by guiverc on 2023-07-16
Likely due to other packages, eg. 

[https://packages.ubuntu.com/focal-updates/graphicsmagick-imagemagick-compat](https://packages.ubuntu.com/focal-updates/graphicsmagick-imagemagick-compat)

which can get installed to fulfill *depends* rule requirements as stated by 1fallen.

Your system is somewhat unknown, you've put this in a Lubuntu area (of UF) where that package was **not** included on [20.04 media]("https://cdimage.ubuntu.com/lubuntu/releases/focal/release/lubuntu-20.04.5-desktop-amd64.manifest"), and what is originally installed varies on installation media (Server, Desktop etc) & then what has been added.

---

### Post by ozark_hillbilly on 2023-07-18
> **guiverc said:**
> 

Your system is somewhat unknown, you've put this in a Lubuntu area (of UF) where that package was **not** included on [20.04 media]("https://cdimage.ubuntu.com/lubuntu/releases/focal/release/lubuntu-20.04.5-desktop-amd64.manifest"), and what is originally installed varies on installation media (Server, Desktop etc) & then what has been added.

Hmmm.... I never selected Lubuntu...

I did state:

Ubuntu 20.04.6LTS

Its not a big deal when the Software Updater includes it I just uncheck it and move on.

---

### Post by #&amp;thj^% on 2023-07-18
if your sure it's not security or bug related that's fine....are you?
Easy way:```

sudo apt-mark hold imagemagick
```
```
imagemagick set on hold.
```
You will now see held package with the above.

Selection states:

The selection state of a package can be:
[list]
   [*]install: this package is marked for installation.
    [*]deinstall (remove): this package is marked for removal.
    [*]purge: this package, and all its configuration files, are marked for removal.
    [*]hold: this package cannot be installed, upgraded, removed, or purged.[/list]

Selection states are used internally by APT and dpkg. For more information about setting selection states, see dpkg --set-selections.

---

### Post by deadflowr on 2023-07-18
I'd run
```
dpkg -l | grep magick
```
to see what, if any, are installed.

I know Software Updater sometimes just outputs a generic-ish name for all related packages,
like if you have some lib package from imagemagick it'll just state update for imagemagick or something.
You would need to look at the package description to find out exactly what package it is.

---

### Post by #&amp;thj^% on 2023-08-01
> **deadflowr said:**
> I'd run
```
dpkg -l | grep magick
```
to see what, if any, are installed.

I know Software Updater sometimes just outputs a generic-ish name for all related packages,
like if you have some lib package from imagemagick it'll just state update for imagemagick or something.
You would need to look at the package description to find out exactly what package it is.

Sometimes we just need to keep repeating the information:
```
apt policy imagemagick
imagemagick:
  Installed: (none)
  Candidate: 8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1
  Version table:
     8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/universe amd64 Packages
     8:6.9.11.60+dfsg-1.6 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages

```
This below belongs to your system>>>(Don't touch)
```
dpkg -l | grep magick
ii  imagemagick-6-common                                        8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1        all          image manipulation programs -- infrastructure
ii  imagemagick-6.q16                                           8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1        amd64        image manipulation programs -- quantum depth Q16
ii  libmagickcore-6.q16-6:amd64                                 8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1        amd64        low-level image manipulation library -- quantum depth Q16
ii  libmagickcore-6.q16-6-extra:amd64                           8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1        amd64        low-level image manipulation library - extra codecs (Q16)
ii  libmagickwand-6.q16-6:amd64                                 8:6.9.11.60+dfsg-1.6ubuntu0.23.04.1        amd64        image manipulation library -- quantum depth Q16

```

---

