---
title: "Can't get 1080 resolution with fglrx drivers"
date: 2015-12-19
forum: General Help
---

### Post by thealchemist886 on 2015-12-19
It looks like I have a problem with my screens edid that the system is not able to detect correctly it's resolution, I was having the same problem with the open source drivers, but could solve it with easy xrandr commands:

```
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DVI-1 1920x1080_60.00
xrandr --output DVI-1 --mode 1920x1080_60.00
```

The problem is that this commands doesn't work correctly with the fglrx drivers and I get this error after the screen blinks, and my resolution doesn't change:

```
xrandr: Configure crtc 0 failed

```

basically the max resolution I can get in the 16:9 format is 1600x900 when my screen accepts up to 1920x1080 and that causes very bad looking graphics and oversized elements.

I found a tutorial that I thought that was going to help me:  [http://hotcashew.com/2013/08/fixing-invalid-edid-in-linux-wit-fglrx/](http://hotcashew.com/2013/08/fixing-invalid-edid-in-linux-wit-fglrx/) But for some reason I'm not able to use other terminals Ctrl+Alt+(F1~F6) because due to the resolution problem the terminals appear black and I can't see anything.

I don't knwo what to do any more with that, using open source drivers is not an option since I need to use 3d acceleration that doesn't work with open drivers.

---

### Post by thealchemist886 on 2015-12-21
bump

---

### Post by QIII on 2015-12-21
Hello!

Could you tell us which release of Ubuntu you are using, the model of the video adapter and how you installed the driver?

---

### Post by thealchemist886 on 2015-12-26
I'm using unbuntu 15.10 and installed the driver through the "programs and updates" windows of "aditional controllers" I'm using the dvi output from the GPU r9 280 I think the problem is a corrupt edid on my screen, since I'm having this resolution problem with all the operating sistems out there (even windows), but I still couldn't find a way to ignore the bad edid, or to use custom configuration

---

### Post by oldos2er on 2015-12-26
Moved to General Help.

---

