---
title: "VLC Snap not loading Ubuntu 24.04"
date: 2024-06-06
forum: General Help
---

### Post by slickvik on 2024-06-06
Hi All, 

While trying to run the VLC snap in 24.04 I get the issue while running in terminal.

```
/usr/share/libdrm/amdgpu.ids: No such file or directory
amdgpu: unknown (family_id, chip_external_rev): (148, 8)
libGL error: failed to create dri screen
libGL error: failed to load driver: radeonsi
VLC media player 3.0.20 Vetinari (revision 3.0.20-1-g2617de71b6)
[000061256f7c3a00] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use QT_QPA_PLATFORM=wayland to run on Wayland anyway.
Qt: Session management error: Could not open network socket
Fontconfig warning: FcPattern object width does not accept value [75 100)
Segmentation fault (core dumped)



```

---

### Post by ActionParsnip on 2024-06-07
Are you using Wayland? If so you could try setting "QT_QPA_PLATFORM=wayland" and test

---

### Post by ap-wtioit on 2024-10-02
Any updates on this, seems the VLC snap is broken for Ubuntu 24.04 (using wayland):

running > QT_QPA_PLATFORM=wayland vlc gives the same output

> /usr/share/libdrm/amdgpu.ids: No such file or directory
amdgpu: unknown (family_id, chip_external_rev): (146, 32)
libGL error: failed to create dri screen
libGL error: failed to load driver: radeonsi
VLC media player 3.0.20 Vetinari (revision 3.0.20-1-g2617de71b6)
[00006519e3d7fb10] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use QT_QPA_PLATFORM=wayland to run on Wayland anyway.
Qt: Session management error: Could not open network socket
Fontconfig warning: FcPattern object width does not accept value [75 100)
Segmentation fault (core dumped)



---

### Post by deadflowr on 2024-10-02
It's the fontconfig that's causing the seg fault.
Try
```
sudo rm /var/cache/fontconfig/*
rm ~/.cache/fontconfig/*
fc-cache -r
```
from here: [https://github.com/keshavbhatt/olivia/issues/95#issuecomment-774747492](https://github.com/keshavbhatt/olivia/issues/95#issuecomment-774747492)
vlc referenced here with above fix as solution: [https://forum.snapcraft.io/t/vlc-in-ubuntu-23-04-broken-fixed-after-fontcache-delete-and-rebuild/35527/9](https://forum.snapcraft.io/t/vlc-in-ubuntu-23-04-broken-fixed-after-fontcache-delete-and-rebuild/35527/9)

---

### Post by ap-wtioit on 2024-10-03
Nice that fixed it for me, many thanks.

---

### Post by wavesound on 2024-11-06
Hi All
New install of Ubuntu  24.04 studio and now vlc has choppy playback on all files.
I setup a new user due to issues with tabs focusing to the right all the time and the new install is just the same.
Tried the usual change the playback to X11 and such.
Uninstalled the player and used the snap version.
Run the code from this thread ( thank you) and at least it starts but still choppy.
My desktop is basic plasma and X11. 


*************************************
this from the command line:
[00007434d4c07a60] main decoder error: Timestamp conversion failed for 57100001: no reference clock
[00007434d4c07a60] main decoder error: Could not convert timestamp 0 for FFmpeg

********************************************
There was a lot of this.


Any more ideas?
Cheers Bob

---

