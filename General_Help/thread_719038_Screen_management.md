---
title: "Screen management"
date: 2008-03-08
forum: General Help
---

### Post by Nelfstar on 2008-03-08
So I was trying to use my television as the default monitor, using a S-Video cable I had that setup, but now that I'm using the monitor on my laptop I'm stuck in 640x480 resolution and I can't change the resolution.

I'm going out to dinner right now, so If you guys could post possible solutions to my problem while I'm out it would be vastly appreciated.

Thank you

---

### Post by pytheas22 on 2008-03-08
First backup your xorg.conf in case something weird happens:
```

cp /etc/X11/xorg.conf ~/Desktop/xorg.conf.bak
```

Then you can try using the Screens and Graphics utility (under the System>Administration menu) to try to change the settings.  If this doesn't work, post your /etc/X11/xorg.conf file and we can try to figure out what's wrong.

---

### Post by Nythain on 2008-03-08
make and model of the video card and tv help :)

---

