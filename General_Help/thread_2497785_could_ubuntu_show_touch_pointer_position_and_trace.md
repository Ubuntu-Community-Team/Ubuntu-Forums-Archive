---
title: "could ubuntu show touch pointer position and trace?"
date: 2024-05-17
forum: General Help
---

### Post by fox8171 on 2024-05-17
Hi there,
we are using a USB touch display on a ubuntu 22.04 PC. 
it is a multitouch capacitive touch panel, touch IC is iLitek ili2511.

we need to know whether it can use 10 points touch. but the iLitek do not have any tool for the testing on linux system.
first we try drawing tool. but drawing tool on Linux can only support single point touch drawing.(windows can support multi point drawing at the same time)
second, we use touchegg to improve gesture. there is 5 fingers gesture can be set at maximum. and 5 fingers works. but we still have no idea for more than 5 points touch works or not.

i'm thinking whether ubuntu can show touch pointer position and trace as android phone?
as the pictures below, it can open the "pointer position" in "developer option" on a Android phone. then it shows touch point and trace.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293785&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293784&stc=1[/IMG]

---

### Post by MAFoElffen on 2024-05-18
I know that in Xorg X11 you can use xev and xinput... That will show keyboard and mouse inputs, but also works with touchscreen. In Xorg, touchscreen events are not part of the core, it was added later, so emulate pointer events.

In wayland, Touchscreen had been around for awhile, so the touch events were added as part of the core. It is touch-down, touch-up, and multi-touch aware. It also supports gestures. But for intercepting touch input... I remember that as of 2017, it was said there was no way (then) to do that yet. That was 7 years ago... That you could probably do it by intercepting calls through dbus, and alternately creating pseudo input using the uinput module... 

What now, I think of is like ipts (Intel Precise Touch & Stylus)... With ipts-show
RE: [https://pkg.go.dev/github.com/linux-surface/iptsd#section-readme](https://pkg.go.dev/github.com/linux-surface/iptsd#section-readme)
but that was written for MS Surface Pro and similar hardware running Linux. I don't know that it would work for your device.

I hear that Touchscreen multi-touch and gestures works better under KDE Plasma 6, for Wayland, BUT... When we testing DEV Noble 24.04, Noble Kubuntu wasn't scheduled to release with Plasma 6. (A few of us tried to build it to test... There were some challenges.)
RE: [https://ubuntuforums.org/showthread.php?t=2493725](https://ubuntuforums.org/showthread.php?t=2493725)

---

