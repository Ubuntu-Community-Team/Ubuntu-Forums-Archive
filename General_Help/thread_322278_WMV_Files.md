---
title: "WMV Files"
date: 2006-12-20
forum: General Help
---

### Post by xenoix on 2006-12-20
Hey, i have been having some problems installing the wmv codecs on ubuntu to play wmv files.

Basically nothing is working. Can anyone tell me what to install (preferably by apt-get) to get what ever is needed to play .wmv files.

Cheers

---

### Post by brianh57 on 2006-12-20
The package you need is W32codecs and I think I got it from the debain repository.  It's been a while though so I'm not sure about that.  I can watch .wmv's fine using Kaffeine on Kubuntu Dapper

Edit: I found the place where I found the answer to this --  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by kevinatkins on 2006-12-20
I'm assuming you're using Totem to play your media files. By default, Ubuntu uses the GStreamer engine for media playback with Totem. I found I had to use the Xine engine instead - run up Synaptic, and replace totem-gstreamer with totem-xine (it may say that ubuntu-desktop needs to be removed - don't panic, this is just a meta package - well, my system didn't break when I removed it, anyway!). Then install the w32-codecs package (think you need multiverse enabled). Now you should be good to go. If you don't fancy mucking up Totem, you can always install the xine library and user interface instead, along with the codecs, and use xine as your standalone media player.

---

