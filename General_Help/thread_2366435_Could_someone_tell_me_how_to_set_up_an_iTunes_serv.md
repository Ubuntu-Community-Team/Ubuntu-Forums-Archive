---
title: "Could someone tell me how to set up an iTunes server?"
date: 2017-07-17
forum: General Help
---

### Post by jakr2 on 2017-07-17
I have s server running ubuntu 16.04 with no GUI. I'd also like to be able to set up a DLNA server for the iTunes server.

---

### Post by BenginM on 2017-07-17
Salutations!

setup a DAAP using forked-daapd , #see man forked-daapd

---

### Post by jakr2 on 2017-07-18
apt-get install english

---

### Post by oldos2er on 2017-07-18
If you have a question about Sary.sa's answer to your original question, please ask it directly. English is not everyone's native language.

```
$ apt show forked-daapd
Package: forked-daapd
Version: 24.2-1
Priority: optional
Section: universe/sound
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 849 kB
Depends: libantlr3c-3.2-0 | libantlr3c-antlrdbg-3.2-0, libasound2 (>= 1.0.18), libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavcodec57 (>= 7:3.2) | libavcodec-extra57 (>= 7:3.2), libavfilter6 (>= 7:3.2) | libavfilter-extra6 (>= 7:3.2), libavformat57 (>= 7:3.2), libavutil55 (>= 7:3.2), libc6 (>= 2.14), libconfuse1 (>= 3.0+dfsg~), libcurl3-gnutls (>= 7.16.2), libevent-2.0-5 (>= 2.0.10-stable), libgcrypt20 (>= 1.7.0), libgnutls30 (>= 3.5.3), libgpg-error0 (>= 1.14), libjson-c3 (>= 0.10), libmxml1, libplist3 (>= 1.11), libprotobuf-c1 (>= 1.0.1), libpulse0 (>= 5.0), libsqlite3-0 (>= 3.6.12), libswscale4 (>= 7:3.2), libunistring0, zlib1g (>= 1:1.1.4), avahi-daemon (>= 0.6.31-3~), adduser, lsb-base (>= 3.0-6), psmisc
Recommends: libavcodec-extra
Homepage: http://github.com/ejurgensen/forked-daapd
Download-Size: 245 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu zesty/universe amd64 Packages
Description: DAAP/DACP (iTunes) server, support for AirPlay and Roku devices
 forked-daapd is an iTunes-compatible media server, originally intended
 as a rewrite of Firefly Media Server (also known as mt-daapd).
 .
 It supports a wide range of audio formats, can stream video to iTunes,
 XBMC and other compatible clients, has support for Apple's Remote
 iPhone/iPod application and can stream music to AirPlay devices like
 the AirPort Express.
 .
 It also features RSP support for Roku's SoundBridge devices and MPD support for
 Music Player Daemon clients.
 .
 Built-in, on-the-fly decoding support enables serving popular free music
 formats like FLAC, Ogg Vorbis or Musepack to those clients that do not
 otherwise support them.
```

---

### Post by BenginM on 2017-07-18
... You're running a server it should be easy to install a DAAP server ...

---

