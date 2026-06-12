---
title: "Vertical synchronisation : no way to make it work !"
date: 2008-06-09
forum: General Help
---

### Post by ®om on 2008-06-09
Hi,

In nvidia-settings, I have enabled Sync to VBlank :
[img]http://www.uploadgeek.com/uploads456/0/nvidia-ogl.png[/img]

But there are still vertical synchronisation problems : when I move a window horizontally, I have horizontal lines (typically a vsync problem), same problem while playing videos...

Several people have exactly the same problem (see my post in French).

How to make the vsync working ?

My problem in French : [http://forum.ubuntu-fr.org/viewtopic.php?id=220393](http://forum.ubuntu-fr.org/viewtopic.php?id=220393)
My post on nvidia forums (and some interesing answers) :
[http://www.nvnews.net/vbulletin/showthread.php?p=1660985](http://www.nvnews.net/vbulletin/showthread.php?p=1660985)

Some screenshots of the problem :

WITH COMPIZ:
[img]http://www.uploadgeek.com/uploads456/0/Capture-7.png[/img]

WITHOUT COMPIZ:
[img]http://www.uploadgeek.com/uploads456/0/Capture-8.png[/img]




That's a general vsync problem, in desktop and in videos.

Now, for videos, there is maybe an option.

In VLC (for example), in fullscreen, with compiz enabled, sometimes I can change the video opacity (Super+middle_mouse), which is rendered in real time, and sometimes it doesn't work (while the opacity in memory changes, because I have just to "zoom" and the screen is refreshed, and the opacity is applies). To resume, 2 cases :
- (a) I can change opacity in fullscreen
- (b) I can't

I explain that because I have no VSync problem in video when I can't change opacity.
- (a) : can change opacity &#8594; VSync problems
- (b) : can't change opacity &#8594; no VSync problems

The problem is that I don't know how to choose if I want to be in case (a) or case (b). It's quite random (today since my last reboot, it seems that I am always in case (a), which is bad).

In VLC I choose XVideo.
In nvidia-settings, Sync to VBlank is enabled both in XVideo and OpenGL, and nvidia-settings -l is applied before launching compiz.
My card is GeForce8600GS, my drivers are nvidia-glx-new from ubuntu repositories (hardy).
```
$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600M GS/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
```

Without the case (b), I have absolutely no solution to watch videos with a correct vertical synchronisation.
(except metacity --replace, where videos are ok, but moving windows is not ok, but I've heard it's normal)


EDIT: For the video problem, I just found : CCSM &#8594; General Options &#8594; General &#8594; Enable "Unredirect fullscreen windows" :)


Disabling Sync to VBlank in nvidia and enabling it in ccsm doesn't work (it's better sometimes, but it doesn't guarantee the vsync -can be interupted-, for example if you use 16x aa and 16x anisotropic, even cube rotating will show tearing effects)


Please help me :)

Do you have a solution for having a correct vertical synchronisation :
- on the desktop, for moving windows for example
- for video playing


Thank you very much for your help if you have a solution !

®om

---

