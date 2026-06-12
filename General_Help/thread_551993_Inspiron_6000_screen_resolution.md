---
title: "Inspiron 6000 screen resolution"
date: 2007-09-15
forum: General Help
---

### Post by wylfing on 2007-09-15
I decided to install Ubuntu on my Dell Inspiron 6000 laptop today. Everything pretty much worked out of the box except for wireless (which I solved pretty easily) and the screen resolution. 

I have the ATI Radeon Mobility, so first step was to install fglrx. Everything about that went fine, grand responses from fgl_glxgears and glxgears, etc. But when I tried to set the screen resolution it wouldn't go higher than 1280x800. Now that's not exactly *bad*, but I would like to get it up to 1680x1050 if possible. (The screen itself is capable of 1920x1200.)

I ran ```
dpkg-reconfigure xserver-xorg
``` in order to enable 1920x1200 and 1680x1050, and those choices show up in the Modes lines of xorg.conf. It seems, however, that X simply rejects anything above 1280x800. Xorg.0.log shows only resolutions 1280x800 and lower being registered -- no mention at all of the higher ones.

Even though X is supposed to figure out virtual size on its own, I tried specifying a virtual size of 1680x1050 to see what would happen, just in case X was getting this wrong for some reason and rejecting higher resolutions on this basis. I checked Xorg.0.log and yes, the new virtual size was accepted, although it still rejected 1680x1050. (The screen real estate was indeed increased to 1680x1050, but the on-screen space was still restricted to 1280x800, so that I had to scroll around the desktop to see it all.)

Has anybody with the same (or similar) laptop managed to get higher than 1280x800 resolution? Is this a limitation of the ATI driver?

---

### Post by karlec on 2007-10-26
My initial install of Gutsy defaulted to the 1920x1200 res.  Thinking that I was really straining my eyes too much, I decided to change to 1680x1050 and now it is completely hosed.  After the restart it refuses to go to anything above 640x480.

---

