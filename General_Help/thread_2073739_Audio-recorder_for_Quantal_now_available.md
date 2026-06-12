---
title: "Audio-recorder for Quantal now available"
date: 2012-10-20
forum: General Help
---

### Post by moma on 2012-10-20
Hello all,
I have upgraded audio-recorder for Ubuntu 12.10 and Fedora 18. 
It uses now [Gstreamer 1.0]("http://www.h-online.com/open/news/item/GStreamer-1-0-released-1716578.html"), one of the first real apps to do that!

[[img]http://bildr.no/thumb/1299388.jpeg[/img]](http://bildr.no/view/1299388)

Get ready-made packages for Quantal from:
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

Source code:
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

Test and love it. Report bugs if found. You are very welcomed.

BTW: Please help to update the translations on 
[https://translations.launchpad.net/audio-recorder/trunk](https://translations.launchpad.net/audio-recorder/trunk)

ps. Fedora 18 needs a package maintainer.
See the fedora/audio-recorder.spec file in the source.

Most kindly
  Moma Antero

---

### Post by moma on 2012-10-28
Re-hi,
I pumped a new version (0.9.7) to launhcpad.net because a.r behaved strangely with Totem Movie Player (and its DBus-interface plugin). The fix is not perfect but usable. I should make a test-case and send it to the devs of Totem.

[[img]http://bildr.no/thumb/1305665.jpeg[/img]](http://bildr.no/view/1305665)

Other fix:
A.r will now remember lastly used media players. Earlier it forgot all but Rhythmbox and Banshee.

The compilation on Launchpad should be ready within two hours.

A smal bug: The programs reports wrong version#. The package has version 0.9.7 while the program reports 0.9.6 (in its About-dialog). Not a big deal. I forgot to run ./configure after last update of configure.in. Will fix it for 0.9.8. (we are almost at 1.0 folks!).

---

### Post by moma on 2012-11-05
Some users where unable to use AR 0.9.7 because it failed to find configuration settings in the GSettings-registry (GNOME uses DConf as the actual backend for GSettings).

More info in [bug #1074928]("https://bugs.launchpad.net/audio-recorder/+bug/1074928").

[Version 0.9.8]("https://launchpad.net/audio-recorder") should fix this bug. Bug closed.

[[img]http://bildr.no/thumb/1315713.jpeg[/img]](http://bildr.no/view/1315713)

ps. I really recommend to see [this video..]("http://www.youtube.com/watch?v=W2LGmY796wQ&t=14m10s") about power of JuJu (firing and migrating services) on Ubuntu. It's really awesome stuff.

---

### Post by moma on 2012-11-18
--deleted--

---

