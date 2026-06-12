---
title: "vlc interface unresponsive after using it once and wont play videos"
date: 2018-06-25
forum: General Help
---

### Post by jimbolaya on 2018-06-25
I'm running Ubuntu 16.04 with a Mate desktop. This instance has been upgraded from 12.0? to 16.04.

I'm running amdgpu-18.10-572953, this is an NFS client

I have two issues when running vlc.

When I attempt to update any option from Tools | Preferences, the interface is no longer usable. I can move the window around and push the window decoration buttons, but clicking anywhere else doesn't work. This is what it looks like when I start it this way:

```
$ vlc
VLC media player 2.2.7 Umbrella (revision 2.2.2+git20170721+r59033+56~ubuntu16.04.1)
[0000000002048148] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "topmenu-gtk-module"
setNativeLocks failed: Resource temporarily unavailable
setNativeLocks failed: Resource temporarily unavailable
setNativeLocks failed: Resource temporarily unavailable

```

with the last line going on ad-infinitum until I kill the process using "kill -9 <pid>". This also happens when I play any music file.

Second, if I attempt to play any video file, I get the following:

```
$ vlc
VLC media player 2.2.7 Umbrella (revision 2.2.2+git20170721+r59033+56~ubuntu16.04.1)
[000000000145e148] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "topmenu-gtk-module"
[000000000156a858] dbus interface error: poll() failed: Interrupted system call
[000000000156a858] dbus interface error: poll() failed: Interrupted system call
[000000000156a858] dbus interface error: poll() failed: Interrupted system call
[000000000156a858] dbus interface error: poll() failed: Interrupted system call
setNativeLocks failed: Resource temporarily unavailable
setNativeLocks failed: Resource temporarily unavailable
[00007f32f404a1d8] vdpau_avcodec generic error: decoder profile not supported: 7
```

Some other posts have said to set video output to "XVideo output (XCB)" but that has had no effect as far as I can tell.

Any pointers for either issue would be appreciated.

---

