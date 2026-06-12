---
title: "[SOLVED] compiz not working in ubuntu 7.10"
date: 2007-12-27
forum: General Help
---

### Post by uroskriznar on 2007-12-27
Hello.

I am using ubuntu 7.10 and Compiz isn't working. My graphic card is ati radeon 9600 and I installed the ati driver.

uros6@uros6-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7170 Release

uros6@uros6-desktop:~$ glxinfo | grep direct
direct rendering: Yes

When I go to System -> Prefereces -> Apperance -> Visual Effects and select normal or extra I get this messege:
The Composite extension is not available

Can someone please help ???

---

### Post by overdrank on 2007-12-27
> **uroskriznar said:**
> Hello.

I am using ubuntu 7.10 and Compiz isn't working. My graphic card is ati radeon 9600 and I installed the ati driver.

uros6@uros6-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7170 Release

uros6@uros6-desktop:~$ glxinfo | grep direct
direct rendering: Yes

When I go to System -> Prefereces -> Apperance -> Visual Effects and select normal or extra I get this messege:
The Composite extension is not available

Can someone please help ???

Hi and have you tried to install xgl?

---

### Post by family on 2007-12-27
Hello, I am having a similar problem; to a point. Sorry to stick my head into this thread but I don't have an ATI card. Compiz Fusion stopped working for me after I did a clean install of Gutsy, for no reason at all.
```

family@Manual:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```
The first time I installed Gutst, it used to return;
direct rendering: Yes
or something like that.
It was suggested that I install the xserver-xgl package; no luck.
I removed everything compiz-related I cound find in Synaptic (even vague packages like lbwnck, libcm7, compiz-bcop, compiz (well, it *is* a metapackage...).
Then, I edited my sources.list so that the only repo in the whole thing was the feisty repo forlong's blog suggests. I reinstalled all of those packages.; no luck.
I have an Intel Chipset (I think thats what it's called), here's my graphics card;

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

(For your ATI card problem, try using Alberto Milone's Envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))

---

### Post by zhouxing on 2007-12-27
to:  uroskriznar

I guess that you could post your xorg.conf here for more information. even if you have installed the driver properly, you still need to setup in xorg.conf

---

### Post by flamer on 2007-12-27
I have the same problem with radeon9600. Copmpiz fusion stops working if I use a  driver

I will post my xorg.conf later beacuse currently I'm not on my computer

---

### Post by uroskriznar on 2007-12-27
I solved the problem by installing xgl and using Envy. Compiz is working now. Thanks!!!

But now Pidgin does not display anything. Just plain gray. Also my keyboard keys got mixed up. Strange???

---

### Post by uroskriznar on 2007-12-28
Everything is working properly with my new ati driver (Envy really helped), but there seems to be another problem now - VLC and other media players are working slowly. Does anyone have an idea what might be wrong?

---

### Post by overdrank on 2007-12-28
> **uroskriznar said:**
> Everything is working properly with my new ati driver (Envy really helped), but there seems to be another problem now - VLC and other media players are working slowly. Does anyone have an idea what might be wrong?

I have seen that in a xgl session the video performances is reduced. Try and turn off compiz an see if the performance improves.

---

### Post by uroskriznar on 2007-12-28
To overdrank: How do you propose, that I turn off compiz?

I changed the video output modules in VLC to X11 and the video performance is a little better, but not in full screen mode. I will inform you if I find out a better solution.

---

