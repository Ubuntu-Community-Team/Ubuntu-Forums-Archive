---
title: "How to enable multi-touch on touch screen laptop."
date: 2013-09-05
forum: General Help
---

### Post by odror on 2013-09-05
Harware: HP Envy TouchSmart 17t-j000
OS: LiveCD 13.10 and 13.04

I just got this new laptop. Before installing ubuntu I tried the LIve CD of 13.04 and the latest daily for 13.10

Basic function of touch screen (moving the cursor and selecting. The equivalent of left click) did work with both. Multi-touch gestures did not work. In particular scrolling and magnifying in firefox.

How do I enable these additional multilouch gestures. Am I missing a driver?. I thought By 13.10 multi-touch comes as default.

Any help will be appreciated.

-Thanks

---

### Post by internalkernel on 2013-09-08
Search for Grab and Drag in Firefox add-ons... that will help with the scrolling feature, magnification is another story. I think there's several issues present here. I've noticed that Unity supports certain gestures while specific apps do not.

---

### Post by odror on 2013-09-08
I have got the 3-4 touch gestures from Unity to work. I am looking for the basic 2 touch gesture like universal scrolling and pinch to zoom. I would like to use it with Chrome as well.

---

### Post by internalkernel on 2013-09-08
Understandable... I just got a touchscreen laptop last week, so I'm learning all this at the moment as well. It seems that multitouch is still a bit finicky.

According to this page: 

[https://wiki.ubuntu.com/Multitouch/TouchpadSupport](https://wiki.ubuntu.com/Multitouch/TouchpadSupport)

If you go into Mouse and Touchpad Settings, disable tap to click and two finger scrolling, that is supposed to enable it for the touchscreen.

Although, depending on your setup you may be afflicted with this bug:

[https://bugs.freedesktop.org/show_bug.cgi?id=56578](https://bugs.freedesktop.org/show_bug.cgi?id=56578)

This was the problem I was having... Double clicking on the screen would work but only for a short time. Changing the mouse settings had no effect.

I followed these instructions to fix:

[http://askubuntu.com/questions/339365/ubuntu-13-04-touch-screen-points-though-doesnt-click](http://askubuntu.com/questions/339365/ubuntu-13-04-touch-screen-points-though-doesnt-click)

After applying the above fix, everything has been working as expected. Touchscreen double clicks, drags, and single click with no issues. Right click is a whole nother story... 

HTH

---

