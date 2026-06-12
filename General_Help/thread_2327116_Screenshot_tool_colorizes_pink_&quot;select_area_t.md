---
title: "Screenshot tool colorizes pink: &quot;select area to grab&quot; includes area shadow in image"
date: 2016-06-07
forum: General Help
---

### Post by swarup on 2016-06-07
Using Ubuntu 14.04, 
1. Open screenshot
2. Choose "Select area to grab" option
3. Select area (as you do this there is visual indication of the area)
4. Look at the file - note that the shaded area is included in the image produced

After having taken a screenshot of a part of my screen which is marked/shown by a pink layer, this pink layer can be seen on the screenshot itself.

This exact issue was reported in three bugs in 2011 pertaining to Ubuntu 11.04. Now I am finding the exact same issue with 14.04. 

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/724491](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/724491)
[https://bugs.dogfood.paddev.net/ubuntu/+source/gnome-utils/+bug/755207](https://bugs.dogfood.paddev.net/ubuntu/+source/gnome-utils/+bug/755207)
[https://bugs.dogfood.paddev.net/ubuntu/+source/gnome-utils/+bug/743176](https://bugs.dogfood.paddev.net/ubuntu/+source/gnome-utils/+bug/743176)

Is there a solution? Or does it again need to be reported as a bug?

---

### Post by vasa1 on 2016-06-07
The first launchpad bug you cited was marked as a duplicate of [https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/743176](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/743176). Even after a fix was released according to comment [#15]("https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/743176/comments/15"), some users are still reporting the issue.

If you have a Launchpad account you could mark the bug I linked to as "affects me too" and **if** you have some additional information you may enter it as a comment there.

In the meantime, try other screenshot tools such as *xfce4-screenshooter* or *scrot*. Both are available in the standard repos. You'll need to have "Universe" enabled in your software sources.

Edit: how do you take your screenshot? Is it via compiz?

Please also try this: open a terminal and run

```
gnome-screenshot -a
```

---

### Post by swarup on 2016-06-08
1. I do have a Launchpad account and will report that the same issue is now occurring in 14.04. 
2. I use screenshot a lot, multiple times a week, and today is the first time I experienced this. So perhaps something that came via the Update Manager has created this issue.
3. Yes, I did download and start using a couple of other screenshot tools earlier tonight. One called Shutter is working really nicely.
4. I don't use compiz when I take screenshot, so far as I am aware. I just open screenshot straightaway.
5. When I opened screenshot using the terminal command "gnome-screenshot -a", then it worked normally. Thank you. Wouldn't want to have to do that every time though! I am aware one can make scripts for these things and assign them to icons, having done this years ago. But I'd have to refresh myself on how this is done...

---

### Post by vasa1 on 2016-06-08
> **swarup said:**
> 1. I do have a Launchpad account and will report that the same issue is now occurring in 14.04. 
2. I use screenshot a lot, multiple times a week, and today is the first time I experienced this. So perhaps something that came via the Update Manager has created this issue.
3. Yes, I did download and start using a couple of other screenshot tools earlier tonight. One called Shutter is working really nicely.
4. I don't use compiz when I take screenshot, so far as I am aware. I just open screenshot straightaway.
5. When I opened screenshot using the terminal command "gnome-screenshot -a", then it worked normally. Thank you. Wouldn't want to have to do that every time though! I am aware one can make scripts for these things and assign them to icons, having done this years ago. But I'd have to refresh myself on how this is done...
Shutter is said to be feature-rich and installing it makes sense if you use its features.

As for > I am aware one can make scripts for these things and assign them to icons, having done this years ago. But I'd have to refresh myself on how this is done...I don't assign scripts to icons. I prefer keyboard shortcuts:
PrntScrn for a whole screen immediate grab
Super-PrntScrn for a time-delayed grab (useful for dropdown menus, etc)
Shift-PrntScrn for grabbing an area.

I also add a timestamp without spaces (which gnome-screenshot uses abundantly):```
gnome-screenshot -p -w -d 10 -f ~/Desktop/Screenshots/"$(date +%Y%m%d%H%M%S)".png
```takes a screenshot of the active _w_indow including the mouse _p_ointer after a _d_elay of 10 s and saves the file to *~/Desktop/Screenshots* with a timestamp.

---

### Post by swarup on 2016-06-08
I just checked this "Shift-PrntScrn for grabbing an area", and it works perfectly, using the gnome screenshot and not leaving me with a pink overlay on the image. That is great!

Thanks for your help and I'll mark this thread as solved.

---

