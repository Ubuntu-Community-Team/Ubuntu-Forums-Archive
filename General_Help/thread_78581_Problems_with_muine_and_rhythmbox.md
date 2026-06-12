---
title: "Problems with muine and rhythmbox"
date: 2005-10-18
forum: General Help
---

### Post by Titeuf on 2005-10-18
Hi, I've just installed breezy and installed all stuff for mp3 playback and so on (followed the guide in System->Help and also tried it with EasyUbuntu)
But I have two strange problems:
[LIST=1]
[*]When I import my music in muine it only shows 5 albums of ~20.
[*]Both muine and rhythmbox (so I assume this is a gstreamer problem) can play fine almost all mp3's, but there is one that doesn't work: with rhythmbox it displays an exclamation mark in front of it and in muine it shows an error message with: "There were no decoders found to handle the stream, you might need to install the corresponding plugins". All my other mp3's work fine, even those of the same album as they were encoded in the same way.
Beep-media-player doesn't have a problem to load and play all my mp3's.
[/LIST]

Some things to note:
[LIST]
[*]All my mp3's are on an ext3 partition on a external USB2 hd
[*]All of them were tagged with easytag and contains ID3v1 and v2 tags. Every mp3 also contains the album cover. They are displayed correctly in muine.
[/LIST]

If anyone can help, I would be glad to hear

---

### Post by hounddog32 on 2005-12-04
I had a similar problem which I fixed by going to System > Preferences > Multimedia Systems Selector and changinf teh sound output to ALSA from ESD (which isn't running by default on my system. 

YMMV

---

### Post by Titeuf on 2005-12-04
[QUOTE=hounddog32]I had a similar problem which I fixed by going to System > Preferences > Multimedia Systems Selector and changinf teh sound output to ALSA from ESD (which isn't running by default on my system. 

YMMV[/QUOTE]
Thanks for trying, but this doesn't solve my problem.
It's a know bug in gstreamer: [bug 320114](http://bugzilla.gnome.org/show_bug.cgi?id=320114)

---

