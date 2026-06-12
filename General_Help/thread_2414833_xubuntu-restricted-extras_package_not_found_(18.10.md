---
title: "xubuntu-restricted-extras package not found (18.10)"
date: 2019-03-15
forum: General Help
---

### Post by Syncope on 2019-03-15
Hi everyone, after some shenanigans in xubuntu 18.04, I decided to reinstall the system and give 18.10 a chance. Everything is smooth, but when I attempted to install xubuntu-restricted-extras, as I'm used to do it first thing on a fresh system, I got "package not found" error. I tried to look for it in synaptic, and there's only xubuntu-restricted-addons.
Is the package no longer available in 18.10? Are these codecs & fonts and what not installed some other way? I can't find any info on this.

---

### Post by Frogs Hair on 2019-03-15
Open software & updates and enable the partners and independent repositories and try again. If using synaptic look in repositories from the drop-down menu.

---

### Post by Syncope on 2019-03-15
I have Canonical partners selected (even source), that's the first thing I do after downloading updates.

---

### Post by deadflowr on 2019-03-15
I don't see it either.
But you can just install ubuntu-restricted-extras since that's what it installs anyway.

---

### Post by again? on 2019-03-15
In 18.04 xubuntu-restricted-extras is marked as a transitional package, which means it is being renamed or replaced.
So in 18.10 you use ubuntu-restricted-extras as [deadflowr]("https://ubuntuforums.org/member.php?u=1276577") said.

You can see in 18.04 it points to another [metapackage]("https://help.ubuntu.com/community/MetaPackages").
My 18.04 output:
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt depends xubuntu-restricted-extras**
xubuntu-restricted-extras
  Depends: ubuntu-restricted-extras

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt depends ubuntu-restricted-extras**
ubuntu-restricted-extras
  Depends: ubuntu-restricted-addons
  Recommends: libavcodec-extra
    libavcodec-extra57
  Recommends: ttf-mscorefonts-installer
  Recommends: unrar

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt depends ubuntu-restricted-addons**
ubuntu-restricted-addons
  Recommends: chromium-codecs-ffmpeg-extra
  Recommends: gstreamer1.0-fluendo-mp3
  Recommends: gstreamer1.0-libav
  Recommends: gstreamer1.0-plugins-ugly
  Recommends: gstreamer1.0-vaapi
```
By default in Ubuntu, recommends are considered dependencies.

---

### Post by Syncope on 2019-03-16
I installed ubuntu-restricted-extras and it went fine.

Thanks for help!

---

