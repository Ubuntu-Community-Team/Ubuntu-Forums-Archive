---
title: "Black screen, only a mouse cursor, after login (Kubuntu 24.04)"
date: 2024-10-05
forum: General Help
---

### Post by gamelord122 on 2024-10-05
As far as I can tell, the only system-level thing I did was update the KDE platform via Discover.  I noticed that Street Fighter 6, via Proton, was running pretty much locked at 50 FPS no matter what settings I put it on, and if you know anything about fighting games, that's 10 FPS too low.  I booted up another game, Divinity: Original Sin II, to see if that was desktop-wide, even though my display refresh rate was set to 144 Hz, because I had noticed my desktop feeling a little sluggish but couldn't put a finger on it.  Before D:OS2 could boot, the computer completely locked up, so I hard power cycled.  On reboot, I can get to a login screen, but once I enter my credentials, I get a black screen and a mouse cursor with no indication of any kind of error on boot.  Recovery mode sees the same thing.

If I leave it on the black screen post-login long enough, it gives me an error box saying startplasma-x11 closed unexpectedly.  There's developer information, but I don't know how to get it from that error box to this forum gracefully.

[IMG]https://imgur.com/a/H8uwAlH[/IMG]
[https://imgur.com/a/H8uwAlH](https://imgur.com/a/H8uwAlH)

I tried "kstart5 plasmashell" from my Ctrl+Alt+F4 shell, and I get the following output.

```
qt.qpa.xcb: could not connect to display
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized.  Reinstalling the application may fix this problem.

Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, wayland-egl, wayland, wayland-xcomposite-egl, wayland-xcomposite-glx, xcb.

Aborted (core dumped)
```

I'm not really sure how to reinstall the application.  I ran a sudo apt update/upgrade, and I'm up to date.  I've tried reinstalling two different packages that might be my xcb, but nothing is changed.  Any ideas how to go about troubleshooting from here?  I'm on AMD and  haven't done anything too crazy with my setup, as far as I know.

---

