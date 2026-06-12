---
title: "NVidia and Direct Rendering"
date: 2008-05-18
forum: General Help
---

### Post by ScottMartin on 2008-05-18
I have a question regarding the reporting of Direct Rending for glxinfo.

Everything seems to work fine. I was looking at glxgears and was expecting a higher score than 4700 seeing as I get around this score using a much older PC using a FX5200.

I have installed the latest driver from Hardy-Proposed (to fix problem with compiz "pink border" issue. Works fine.

(used Envy to install driver), updated to nvidia-glx-new from command line.

If I run $ glxinfo | grep direct, the reply is NO
If I run $ sudo glxinfo | grep direct, the reply is YES

If I run $ glxinfo | grep vendor, NVIDIA displays 2 of 3, where
client glx vendor string is SGI

I have read several postings that removing xserver-glx have solved the "reporting" issue of rending, but I have also read responses that it will also slow down the rendering.

I have found a posting stating that XGL always reports "false" on rendering status:

[https://answers.launchpad.net/ubuntu/+source/xserver-xgl/+question/27148]("https://answers.launchpad.net/ubuntu/+source/xserver-xgl/+question/27148")

Could I get some clarification on this? Is this a reporting issue and all is well, or should I get a better score and how can I remedy this? 

Should I be able to get a YES from glxinfo?

I do have compiz running, will this affect my score?

I have:
Dual Core Intel
NV.8500GT.PCI-E.512M (revised)
1 GIG Ram
U8.04

---

### Post by ibuclaw on 2008-05-18
Compiz will affect 3D rendering heavily.

Most Linux Gamers will agree, it is far better to play games in Gnome/Metacity than Gnome/Compiz.
And sometimes further improvements happen when you play in the Failsafe Terminal!

I don't appear to have direct rendering...hmm, I wonder why?

I have an 256MB NVIDIA 8500GT PCI-Express Card.

Rendering score under Compiz:   5216.560
Rendering score under Metacity: 2690.942 ???
[PHP]
$ glxinfo | grep direct
direct rendering: No
$ sudo glxinfo | grep direct
direct rendering: No
$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
[/PHP]

I suppose I never really think about these things as I'm not a die-hard graphics user.

Although, I had problems upgrading to the "hardy-proposed repository. Some openGL3D stuff won't work as "vendor is not on whitelist" or some other sort.

Pinning it back to the main version helped :D

Regards
Iain

---

