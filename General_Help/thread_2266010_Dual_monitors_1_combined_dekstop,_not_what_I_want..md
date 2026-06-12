---
title: "Dual monitors 1 combined dekstop, not what I want."
date: 2015-02-19
forum: General Help
---

### Post by Ssscrudddy on 2015-02-19
Hi.

Ubuntu 14.04
GPU Nvidia 9600 GSO 512MB

I have 2 monitors running 2 different resolutions. 1 is 1024x768, the other 1920x1080. I like to save stuff I'm working on to the desktop. I would have these items on 1 montior, whilst using the other as my main screen.
The problem is, it treats it as 1 giant composite montior, or rather 1 desktop, with parts of it not accessible to me.

In the screenshopt below (taken with workspaces enabled) you can see 2 desktop backgrounds which represent each monitor (coinciding with their real physical positions). The black bits are off the monitor screens. If I sort the icons, as you can see the desktop icons on the left monitor run off the screen, defeating the object of having them on the desktop in the 1st place.

I would like those icons to confine themselves to the screens, but I cant figure out how to do it. For the record, if I maximise a window, it confines itself to whichever screen it's on.


[IMG]https://lh4.googleusercontent.com/-wYz5HMa0niY/VOW3u4HOauI/AAAAAAAAOxs/uF_xsAQgaGk/w1017-h533-no/dual%2Bmonitors%2Bdiff%2Bresolution.jpg[/IMG]

---

### Post by tgalati4 on 2015-02-19
That's the super desktop concept.  X11, or X-Windows is a 40-year-old graphics framework.  Xorg is the modern version of this framework, but some limitations apply.  Is there a better way to handle multiple displays?  Perhaps, but that is how X functions.

One work-around is to have a clean desktop.  Don't put any icons on the desktop.  This requires some discipline.  You can assign hot-keys as shortcuts for your frequently used applications.  Make a list of them.  You will find that this way of working is quite productive.

Lay out your directories in groups of 12--no more.  It makes finding projects and documents quicker than having 100 icons scattered on the desktop.

Perhaps there is a way to fix your situation.  I don't know of it.

---

