---
title: "Mouse pointer disappears"
date: 2016-08-05
forum: General Help
---

### Post by n-spect-r on 2016-08-05
I was running Lubuntu 15 for about 6 months, just changed to 16 yesterday and now I have this problem.  Any time my screen goes blank, close laptop lid or screensaver time out, when I log back in the mouse pointer is gone.  I can move the mouse around and find the start position, log out and back in and it's back. I found references to this with Nvidia drivers but I have an Intel video card.

Running on an Asus netbook, 2 gigs ram and 64 gig SSD.

---

### Post by David_Wright on 2016-08-05
> **n-spect-r said:**
> I was running Lubuntu 15 for about 6 months, just changed to 16 yesterday and now I have this problem.  Any time my screen goes blank, close laptop lid or screensaver time out, when I log back in the mouse pointer is gone.  I can move the mouse around and find the start position, log out and back in and it's back. I found references to this with Nvidia drivers but I have an Intel video card.

This is a known bug, in the release notes.  Seems odd to me that something this fundamental hasn't been fixed already, but I don't have (1% of) the skills needed to do so.

There are a lot of workarounds at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604) and the one that worked for me (Xubuntu) was:

```
[COLOR=#333333][FONT=monospace]sudo mkdir /etc/X11/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]xorg.conf.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]d/[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]echo -e 'Section "Device"\n Identifier "Card0"\n Driver "Intel"\n [/FONT][/COLOR][COLOR=#333333][FONT=monospace]Option "AccelMethod" "uxa"\nEndSection' | sudo tee [/FONT][/COLOR][COLOR=#333333][FONT=monospace]/etc/X11/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]xorg.conf.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]d/20-intel.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]conf[/FONT][/COLOR]
```

---

### Post by n-spect-r on 2016-08-05
I kept looking and found that if I remove Light-locker the problem is fixed.  Thanks for the reply.

---

