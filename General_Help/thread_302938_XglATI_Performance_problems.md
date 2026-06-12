---
title: "Xgl/ATI Performance problems"
date: 2006-11-19
forum: General Help
---

### Post by TurkVU on 2006-11-19
I have some severe performance issues when running an xgl session in Edgy kubuntu. My standard kde session is just fine. I installed the driver for my ATI Radeon 9700 pro using both methods listed here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
But both give me the same issue. 

Any ideas?

---

### Post by TurkVU on 2006-11-19
^

---

### Post by TurkVU on 2006-11-19
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 PRO Generic
OpenGL version string: 2.0.6174 (8.31.5)

glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9700 PRO Generic

---

### Post by igknighted on 2006-11-19
What are the performance issues you are having?  Is it just laggy?  My initial reaction is that you don't have a composite window manager running, in which case XGL will be laggy, as metacity/kwin are not meant to be used with XGL.  If you are using an XGL session you need to use a composite window manager like beryl or compiz

---

### Post by TurkVU on 2006-11-19
I'm running beryl. The performance issue is in programs opening and in simple things like typing showing up. Also rendering effects like rollover graphics.

---

### Post by TurkVU on 2006-11-19
> **igknighted said:**
> What are the performance issues you are having?  Is it just laggy?  My initial reaction is that you don't have a composite window manager running, in which case XGL will be laggy, as metacity/kwin are not meant to be used with XGL.  If you are using an XGL session you need to use a composite window manager like beryl or compiz

On second thought - it looks like you might be right. For some reason Beryl isn't the window manager when I load my xgl session and I'm not sure how to make it that way...any ideas?

---

### Post by TurkVU on 2006-11-19
Even when I'm running in KDE and everything seems normal I"m getting extremely slow FPS when running glxgears:

glxgears -printfps
1950 frames in 5.0 seconds = 389.731 FPS
1874 frames in 5.0 seconds = 374.769 FPS
1826 frames in 5.0 seconds = 365.169 FPS
1844 frames in 5.0 seconds = 368.769 FPS
1883 frames in 5.0 seconds = 376.566 FPS
1789 frames in 5.0 seconds = 357.772 FPS

---

### Post by CowzRule on 2006-11-19
> **TurkVU said:**
> On second thought - it looks like you might be right. For some reason Beryl isn't the window manager when I load my xgl session and I'm not sure how to make it that way...any ideas?

I also have an ATI card running XGL/Beryl combo and it runs GREAT :mrgreen: 
Here is the guide I followed to install install it:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")
```
glxgears -printfps
24118 frames in 5.0 seconds = 4817.361 FPS
41618 frames in 5.0 seconds = 8299.655 FPS
41627 frames in 5.0 seconds = 8325.154 FPS
41627 frames in 5.0 seconds = 8321.956 FPS
41627 frames in 5.0 seconds = 8324.328 FPS
41074 frames in 5.0 seconds = 8200.300 FPS
41513 frames in 5.0 seconds = 8285.183 FPS
41627 frames in 5.0 seconds = 8315.194 FPS

``````
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 PRO Generic
OpenGL version string: 2.0.6119 (8.30.3)
```

---

### Post by TurkVU on 2006-11-20
Yah - I followed those same steps...still having issues.

---

### Post by TurkVU on 2006-11-20
^

---

### Post by strabes on 2006-11-20
set beryl-xgl to start up with KDE.

---

### Post by TurkVU on 2006-11-20
> **strabes said:**
> set beryl-xgl to start up with KDE.

I have a script that starts beryl-xgl in my autostart directory and it is executable so it runs fine. But for some reason when I run beryl-xgl in a terminal window it tells me that some other window manager is loaded and I beryl can't take over. I've tried this command w/ beryl started and w/o it started...](*,)

---

### Post by igknighted on 2006-11-20
you can try adding --replace to the end, or try running the command 'beryl-manager'.  This should give you the gem in you system tray, then you can click that and select beryl over kwin as the window manager.

---

### Post by WalmartSniperLX on 2006-11-20
I dont know about you but ive tried almost everything to get XGL/Beryl running with my ati X1600pro and nothing really works. ATI offers bad performance in Linux no matter what (their drivers). 

Those scores on glxgears look about normal for an ati card. ;) 

I get around 123fps with the newest driver in glxgears, and I got 2200 when I ran the x.26.x driver release, but it didnt offer any avivo for the x1k. (Dont think it really mattered anyways) :mrgreen:

---

### Post by TurkVU on 2006-11-20
When I run beryl --replace this is the output I get:

beryl --replace
XGL Present
beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :1.0

---

### Post by TurkVU on 2006-11-20
Looks like this thread may have a solution:
[http://www.ubuntuforums.org/showthread.php?p=1785500#post1785500](http://www.ubuntuforums.org/showthread.php?p=1785500#post1785500)

But I'm not sure how to go about switching kernels...any howto's on that?

---

### Post by TurkVU on 2006-11-20
Nope - tried running the 386 kernel and have the same issues...sometimes the xgl session won't let me type in input boxes, all the window borders are gone, and none of the effects are working at all. Like I said before it seems that another window manager isn't allowing beryl to take over. Is there some issue w/ beryl running at high resolutions?

---

