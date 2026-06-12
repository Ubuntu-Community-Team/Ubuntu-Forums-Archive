---
title: "Intel Graphics Problems"
date: 2008-01-23
forum: General Help
---

### Post by patmalcolm91 on 2008-01-23
Hello, this is my second laptop installing linux and am AGAIN having graphics problems. Graphics in ubuntu on both machines are bad, CF works nicely on both, but things like GStreamer, the screensaver, and Wings3D are glitchy.

For example, When i play a video in Gstreamer and drag the window i get tons of fragments, and the actual video stays in the same place until i stop dragging, or if i rotate the desktop cube in CF, the video stays in the same place, behind the windows. Wings3d flashes every time i click, etc. I think it may be something with OpenGL, as VLC works flawlessly (although it doesn't work with my media keys, and i don't like the interface)

My laptop is:
 Gateway M465-E
 Intel Centrino Duo processor
 Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller

Before Ubuntu, i tried Fedora 8 on this laptop, and the Graphics worked great, gstreamer, Wings3D, screensaver, all perfect. But after a week of not being able to get my wireless card working (ipw3945), I went with Ubuntu. This is the family laptop, so i really want my family to get a good first impression of Linux.

my other laptop specs are as follows:
 Dell Inspiron 630m
 Pentium M processor
 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
 

If anyone can point me in the right direction that would be great, (or if they have any advice on getting my wireless card working on fedora that would also be great, as i tried all the howtos i could find). You guys are great, and thanks in advance for any help.

---

### Post by peabody on 2008-01-23
Try setting output driver to x11 in your video players.  This will make video playback eat a lot of cpu, but the output should behave as expected.

Not sure if this was the default in Fedora but it sounds like it was.

To set it for totem, run gstreamer-properties, select the video tab and select x11 (no xv).

---

### Post by patmalcolm91 on 2008-01-24
Thanks, that worked amazing for gstreamer, now how would i go about doing this for the screensaver (and the screensaver mini-preview and other applications? Will I have to modify the settings in each of those programs individually?

---

### Post by peabody on 2008-01-24
Can't help you there, I have the same problems with the mini-preview, though fullscreen screensavers have no problems for me.  Google-earth goes nuts under compiz on my machine.

I was under the impression that GL overlays are just glitchy in compiz.  Would be interested to know if there was a fix.

---

### Post by patmalcolm91 on 2008-01-24
Thanks, I'll look more into the compiz-fusion side of things and see if that's the problem. If it is, I hope they get it fixed soon.

---

