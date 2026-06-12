---
title: "Why do fonts seem absolutely horrible?"
date: 2007-04-13
forum: General Help
---

### Post by jasonwjones on 2007-04-13
I've searched through the forums but haven't really come up with much besides some rather hackish workarounds... it'd be nice if we could have out of the box nice fonts.  I have a 15.4" widescreen laptop, but this was also prevalent when I used to run Dapper on my workstation with a 19" flat-panel: fonts are just absolutely terrible for me in Linux.  Things in Firefox seems to mostly render just fine, but I can't get over that GTK apps and the whole desktop seems a bit 'sloppy'.  I've tried playing with the font, the DPI, the size, everything I can think of.  I've seen some impressive screenshots of the 'improved subpixel rendering' packages but due to upgrade concerns I hate straying too far from the mainline with regard to which packages I put on my machine.  

I'm not really a font guy so I don't know technically how to describe it, but I do know that when I boot into Windows 2000, using its Tahoma font, all dialogs and the system in general just look very clean... but when I boot Linux, the spacing feels wrong, the antialiasing looks sloppy... I even tried to use Tahoma for my font instead of god-knows-what-the-default is, but it still didn't look as 'clean' as it does in Windows.  Has anyone else noticed this, and better yet, is there a way to improve it without adding some weird package or repository?

---

### Post by bashologist on 2007-04-13
I've managed to fix some of my font problems by doing this:
```
sudo dpkg-reconfigure fontconfig-config
Autohinter
Always
No
```
Maybe this helps?

---

