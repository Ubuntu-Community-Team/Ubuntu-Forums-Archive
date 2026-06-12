---
title: "Why when I Decrease/Increase Sound Volume in my OS..."
date: 2023-01-09
forum: General Help
---

### Post by nilovsergey on 2023-01-09
In my kubuntu 20.04 I have  hot keys set for audio volume inc/dec : [https://prnt.sc/X8wvbn5hBSS5](https://prnt.sc/X8wvbn5hBSS5)
From some time When I Decrease/Increase Volume in my OS also sound volume in audacious is also 
decreased/increased at the same time. I dislike this option(actually I did not have it before)...
How can I change it and return to prior state when When I Decrease/Increase Volume in my OS  with hotkeys to to alter volume in audacious?
I have :
```
master@master-at-home:/mnt/Media_sda8/VIDEO/Music_Symfonic$  lsb_release -d; uname -r; uname -i
Description:    Ubuntu 20.04.5 LTS
5.15.0-53-generic
x86_64
master@master-at-home:/mnt/Media_sda8/VIDEO/Music_Symfonic$ kf5-config --version
Qt: 5.12.8
KDE Frameworks: 5.68.0
kf5-config: 1.0
master@master-at-home:/mnt/Media_sda8/VIDEO/Music_Symfonic$ dpkg -s   audacious
Package: audacious
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 1272
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 3.10.1-1build1
Depends: audacious-plugins (>= 3.10.1), dbus, default-dbus-session-bus | dbus-session-bus | dbus-x11, gtk2-engines-pixbuf, libaudcore5 (= 3.10.1-1build1), libc6 (>= 2.4), libgcc-s1 (>= 3.0), libglib2.0-0 (>= 2.37.3), libstdc++6 (>= 4.1.1)
Recommends: unzip
Description: small and fast audio player which supports lots of formats
 Audacious is a fork of beep-media-player which supports Winamp skins
 and many codecs.
 .
 In the default install, the following codecs are supported:
 .
  * MP3
  * Ogg Vorbis / Theora
  * AAC and AAC+
  * FLAC
  * ALAC
  * Windows Media (WMA)
  * WAVE
 .
 Additionally, Audacious is extendable through plugins, and contains
 other useful features like LIRC support. Support for many more codecs
 can also be added through plugins.
 .
 This package contains the core player and its localization.
Original-Maintainer: Debian Multimedia Maintainers <debian-multimedia@lists.debian.org>
Homepage: http://www.audacious-media-player.org/

```Thanks!

---

### Post by MAFoElffen on 2023-01-10
Is this what you are talking about? : [https://askubuntu.com/questions/277105/audacious-uses-volume-control-when-ive-configured-the-media-hotkeys](https://askubuntu.com/questions/277105/audacious-uses-volume-control-when-ive-configured-the-media-hotkeys)

---

