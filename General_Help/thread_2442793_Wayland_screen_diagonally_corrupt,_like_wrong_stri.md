---
title: "Wayland screen diagonally corrupt, like wrong stride / pitch, on Radeon X1400 RV515"
date: 2020-05-07
forum: General Help
---

### Post by dreamlayers on 2020-05-07
I was just trying out Wayland for the first time on my Dell Inspiron 6400 laptop with ATI / AMD Mobility Radeon X1400 graphics (RV515/M54). The screen is corrupt with diagonal lines, like the stride / pitch is wrong. In other words, the code drawing on the screen thinks there is a certain number of bytes per line, and the hardware outputting that uses a different number of bytes per line. So, each line is offset horizontally from the previous line.

This happened with gdm3, GNOME shell, Weston and Sway. GNOME displayed a hardware mouse cursor, which was perfect. This shows that data was properly getting from the GPU to the screen, and it wasn't a video mode issue. The problem must be the way the data was being put into video memory, like I described.

I see a Red Hat bug has been reported: [https://bugzilla.redhat.com/show_bug.cgi?id=1420065](https://bugzilla.redhat.com/show_bug.cgi?id=1420065)

I don't even know how to report a Wayland bug in Ubuntu. It clearly isn't simply a bug in GNOME, Weston or Sway when it affects all 3 of them. Which package do I report on?

BTW. I also tried Wayland on my desktop PC with Nvidia Geforce GT 710 graphics. There I get a hang on boot if I put nvidia-drm.modeset=1 on the kernel command line.

This is in Ubuntu 20.04 and I'm giving up on Wayland for now.

---

### Post by mörgæs on 2020-05-07
One of my rigs runs an RV516. I would not consider feeding it neither Gnome nor Wayland - just give yours a fresh install of X/Lubuntu and I guess it'll be fine.

---

### Post by dreamlayers on 2020-05-07
I normally use Xfce and it's fine. X in general works well.

After observing exactly the same graphical corruption in kmscube and in 5.7.0-rc4 kernel, I assume this is a kernel bug with radeon module DRM KMS. I reported it at [https://bugzilla.kernel.org/show_bug.cgi?id=207619](https://bugzilla.kernel.org/show_bug.cgi?id=207619)

---

