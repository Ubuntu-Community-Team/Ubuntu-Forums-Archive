---
title: "Ubuntu Mate 20.04, DVD not playing with Celluloid, Bourne movie"
date: 2022-07-23
forum: General Help
---

### Post by SciGuy1872 on 2022-07-23
Hi.  I'm trying to play a Hollywood movie with Celluloid--the program states that the file format is not recognized.  I've never tried to play a DVD on my computer before, but now I have a big screen.

```
sudo lshw -short | grep disk

/0/9/0.0.0       /dev/sda         disk           1TB ST1000DM003-1CH1
/0/a/0.0.0       /dev/cdrom       disk           DVD+-RW DS-8A9SH
```

So you can see that the drive is detected.  And I checked that it was mounted in "Disks" app.
The codecs package from the Software Boutique is installed.  I was hoping someone could help me to  install the right file format for the Hollywood movie to play.

---

### Post by DuckHook on 2022-07-23
You probably need to install the codecs and/or the dvd libraries:```
sudo apt install ubuntu-restricted-extras
```…then:```
sudo apt install libdvd-pkg
```…then answer "yes" to all dialogue boxes, then reboot.

BTW, you may also wish to try VLC, an extremely versatile player that comes with many of its own built-in codecs and will often work where other players won't:```
duckhook@Zeus:~$  apt show vlc
Package: vlc
Version: 3.0.16-1build7
Priority: optional
Section: universe/graphics
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <debian-multimedia@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 236 kB
Provides: mp3-decoder
Depends: vlc-bin (= 3.0.16-1build7), vlc-plugin-base (= 3.0.16-1build7), vlc-plugin-qt (= 3.0.16-1build7), vlc-plugin-video-output (= 3.0.16-1build7)
Recommends: vlc-l10n (= 3.0.16-1build7), vlc-plugin-access-extra (= 3.0.16-1build7), vlc-plugin-notify (= 3.0.16-1build7), vlc-plugin-samba (= 3.0.16-1build7), vlc-plugin-skins2 (= 3.0.16-1build7), vlc-plugin-video-splitter (= 3.0.16-1build7), vlc-plugin-visualization (= 3.0.16-1build7)
Suggests: vlc-plugin-fluidsynth (= 3.0.16-1build7), vlc-plugin-jack (= 3.0.16-1build7), vlc-plugin-svg (= 3.0.16-1build7)
Homepage: https://www.videolan.org/vlc/
Task: kubuntu-desktop, kubuntu-full, lubuntu-desktop, ubuntustudio-desktop
Download-Size: 37.3 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
Description: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG-2, MPEG-4,
 DivX, MOV, WMV, QuickTime, WebM, FLAC, MP3, Ogg/Vorbis files, DVDs, VCDs,
 podcasts, and multimedia streams from various network sources.
 .
 VLC can also be used as a streaming server that duplicates the stream it
 reads and multicasts them through the network to other clients, or serves
 them through HTTP.
 .
 VLC has support for on-the-fly transcoding of audio and video formats, either
 for broadcasting purposes or for movie format transformations. Support for
 most output methods is provided by this package, but features can be added by
 installing additional plugins:
  * vlc-plugin-access-extra
  * vlc-plugin-fluidsynth
  * vlc-plugin-jack
  * vlc-plugin-notify
  * vlc-plugin-samba
  * vlc-plugin-skins2
  * vlc-plugin-svg
  * vlc-plugin-video-splitter
  * vlc-plugin-visualization
```

---

### Post by Holger_Gehrke on 2022-07-23
Commercial Video DVDs are partially encrypted using the Content Scrambling System. This is not really aimed at consumers copying discs but more at manufacturers of players having to buy a license from the DVD consortium to get a key. Since these keys are supposed to be secret, there's no good way an open source program can include such a key, so none of them can legally play DVDs in some jurisdictions. There are libraries to get around this but their legality is very dependent on where you are. Since at least in the USA the source code of this library is considered free speech, the libdvd-pkg is a 'hack' of the legal system in that it downloads and compiles the needed library from source. Just offering the compiled binary might get the distributor into trouble. It's very unlikely that you actually need any special codecs, DVDs use standard mpeg2 streams for video and audio.

Holger

---

