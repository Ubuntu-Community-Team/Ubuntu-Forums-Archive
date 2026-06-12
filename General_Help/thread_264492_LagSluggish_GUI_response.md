---
title: "Lag/Sluggish GUI response"
date: 2006-09-24
forum: General Help
---

### Post by cfao on 2006-09-24
I have a problem when I'm in gnome. The response time is kind of slow. When I click on maximize/restore on a window or click on the system panel it takes a second or two to respond. It is very noticeble when clicking the log off/shutdown button (or menu option). Is there any way I can diagnose the source of the problem, or better yet, solve it? This kind of makes the system feel sluggish and ruins the experience.


My system is:
Aopen 1557-GL
Centrino 1.7
2Gb of Ram
Mobility Radeon 9700 128Mb
Running XGL and Compiz

---

### Post by cfao on 2006-09-25
Anyone?

---

### Post by orb9220 on 2006-09-25
Have you installed the video drivers for this chipset?
The default ubuntu drivers are just like the default windows drivers havint only the basic without 3d acceleration etc,,,
 

search on forum for radeon , 9500 etc for thread on installing driver for your video.

---

### Post by sabelsen on 2006-09-25
Have you checked your system monitor to see whether some process is using up a whole lot of cpu cycles? I guess you know about System -> System Monitor. Check resources and CPU history.

---

### Post by cfao on 2006-09-26
I have the latest FGLRX drivers installed and using the top utility with a small delay, I can see that XGL jumps to 100% cpu usage when doing the actions I mentioned. Is there something that I need to change for it to be faster?



```
fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.2 (2.0.5814 (8.25.18))

```

---

