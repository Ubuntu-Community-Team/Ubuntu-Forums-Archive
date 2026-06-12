---
title: "Ubuntu 18.04 Gnome Metacity No Desktop After Update"
date: 2020-02-15
forum: General Help
---

### Post by machalam on 2020-02-15
Hello,

I've performed and update after a month or two on one of my Ubuntu 18.04 desktops. I am using Gnome flashback there with automatic login, all was working flawlessly before.

Now after the update what's happening is that the gnome flashback desktop no longer loads properly: I get a mouse pointer that I can move around that is on an otherwise completely black screen. Interestingly the way to fix the problem is to switch to another console (ctrl+alt+F2 for example) and then immediately switch back to the graphical console again (ctrl+alt+F1), then the desktop appears and all works perfectly fine. It even seems that what I executed by the mouse on the black screen actually really happened (like pressing the right mouse button that displays a context menu).

Standard Ubuntu desktop loads normally on the first attempt without an issue.

I am using proprietary nvidia drivers 435 installed via ubuntu sources. The kernel was upgraded to 5.3 during the upgrade, but even choosing the old 5.0.37 kernel in the grub changes nothing.

Any ideas what could have gone wrong and how to remedy this? Perhaps reinstall the Gnome flashback? Can someone advise how it should be done, what packages I need to reinstall?

Thanks a lot!

---

### Post by machalam on 2020-02-16
OK, so I solved it by changing a few things in the nvidia settings (nvidia-settings), namely I manually chose my monitor and resolution in the X Server Display Configuration (and saved it into the X config file) and under X Server XVideo Settings chose my monitor under sync to this display.

Before that I tried to reinstall most of the packages that the gnome flashback depends on and reinstalled the nvidia drivers, but this didn't help.

---

