---
title: "Looking for command line ScreenShot package"
date: 2020-02-26
forum: General Help
---

### Post by satimis on 2020-02-26
Hi all,

I have been running Gnome-screenshot sometimes.  But I couldn't take a screenshot with a predefined pixel size.  I have been searching a command line screenshot package for a while but I found many suggestions on Internet.

Can any folk online sharing me his/her experience.  What I need is taking a screenshot with my required pixel size.

Thanks in advance.

Regards
satimis

---

### Post by TheFu on 2020-02-26
ImageMagick has **import**.  Lots and lots of options to control it.

---

### Post by GhX6GZMB on 2020-02-26
With "pixel size", I suppose you mean screen resolution, or?

My way is to just take the screenshot (.png) at its current resolution and then resize it manually afterwards.

You could write a script with the following line:

       [B]scrot -o /tmp/clip -e 'xclip -selection clipboard -t image/png < $f'

[/B]followed by a resizing command (don't know of any, but they must out there...).

---

### Post by him610 on 2020-02-27
I am using Xubuntu and one can start the screenshot program three different ways:
Press the Print Screen key
Click on the Screenshot icon
Type xfce4-screenshooter + Enter in a terminal

I would think the other *buntu distros work in a similar fashion.

---

### Post by freebird54 on 2020-02-28
I also get the screenshot, usually with PrintScreen (or CTRL-PrtScrn for selected area shots) and then resize afterwards. With ImageMagick all I need to do to shrink file size appropriately (which might be what you're after) is:

**convert *filename*.png -resize 1920x1080 *filename*.jpg**

which not only resizes down to 1920x1080 (example only - my screen is 3840x2160) but also makes a smaller jpg file out of it. Either or both can be specified separately. As a workflow I find it simpler than trying to force-feed a command line with pre-defined values, as reasons for a screenshot can come up without warning - and this still leaves lots of flexibility for the final outcome.

Freebird54

---

