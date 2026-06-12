---
title: "Since 18.04 to 20.04.1 update, mpv, vlc, etc. dump core for any video file"
date: 2020-12-25
forum: General Help
---

### Post by petersanchez on 2020-12-25
I updated to 20.04.1 recently and things were smooth for the most part. However since the upgrade I am unable to play video files. I normally use mpv but sometimes vlc as well and both dump core whenever trying to play a file.

gdb snippet:

[https://paste.sr.ht/~petersanchez/5eea9a762e1ee64ab6a53d0c0b98d02a21bdf3b5](https://paste.sr.ht/~petersanchez/5eea9a762e1ee64ab6a53d0c0b98d02a21bdf3b5)

Anyone have any ideas on how to resolve this?

Thanks,

Peter

---

### Post by petersanchez on 2020-12-25
Turns out it's due to this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1876219](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1876219)

I can confirm that setting `MESA_LOADER_DRIVER_OVERRIDE=i965` works as a workaround for now.

---

