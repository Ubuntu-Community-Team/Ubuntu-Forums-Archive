---
title: "fglrx and Kernel 3.19"
date: 2015-01-24
forum: General Help
---

### Post by inertiaO on 2015-01-24
I need help to get these two to play together. I have tried downloading Fglrx 14.12 from the AMD site and installing with Kernel 3.19 but it doesn't work and I get a Kernel panic. I need the 3.19 because it supports my Logitech touchpad correctly and previous kernels do not. I was using the open source AMD driver but the jerky video playback on some of my video files is driving me nuts.

Thanks in advance.

A welcome alternative would be to patch the current 3.16 to get my logitech working, if that is possible.

---

### Post by Yellow Pasque on 2015-01-24
I haven't seen any patches floating around out there for 3.19. That doesn't mean they don't exist though. At any rate, the open source driver generally has better video decode acceleration if you have it set up right. Start here:
```
sudo apt-get install mesa-vdpau-drivers vdpau-va-driver vdpauinfo vainfo
```
Check the output of vpdauinfo and vainfo to make sure they report no errors:
```
vdpauinfo
vainfo
```

Then you can test video playback using a video player that supports vdpau, like mplayer or mpv. Optionally, you can use the latest version of the open source radeon driver from the "oibaf" PPA (which also has updated mpv):
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by inertiaO on 2015-01-24
I think that has actually solved the video playback issue! Thanks a lot.

I jumped the gun a bit and updated the graphics drivers oibaf ppa but it crashed Kodi upon video playback. I purge the PPA and just used the current 1410 versions and it seems a lot better.

Thanks!

---

