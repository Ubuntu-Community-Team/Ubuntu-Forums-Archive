---
title: "Beryl/Compiz AIGLX/Xgl questions"
date: 2006-11-22
forum: General Help
---

### Post by johann_p on 2006-11-22
There are a lot of guides out there but I must admit I am still quite puzzled. Guides often just give a couple of commands or config file settings but do not really explain what is going on.
So here a few questions -- Note: they all relate to Edgy on a 32 bit system.

* AIGLX comes with Edgy -- but with what card/driver combinations does it work? As it seems, it does not work with the current Nvidia (proprietary) drivers. 
* The beta NVidia drivers work with Beryl, but it seems AIGLX is not even used then. What is going on? Is it possible to choose whether or not to use AIGLX with a beta Nvidia driver? How? What would be the differences?
* Compiz and Beryl seem to be alternatives: what are the differences? Is there an impact on performace or what kind of applications work?
* Xgl, AIGLX, using the drivers features directly seem to bee alternatives of how to get 3D and effects to work. What are the differences? What is the impact on running applications like 
  - 3D games in windows
  - video players
  - remote session viewers

Are these questions answered already somewhere?

---

### Post by 23meg on 2006-11-22
> 
* AIGLX comes with Edgy -- but with what card/driver combinations does it work? As it seems, it does not work with the current Nvidia (proprietary) drivers.It does work with the latest proprietary Nvidia drivers, if you have supported hardware.

> * The beta NVidia drivers work with Beryl, but it seems AIGLX is not even used then. What is going on? Is it possible to choose whether or not to use AIGLX with a beta Nvidia driver? How? What would be the differences?You can start Beryl with --force-aiglx to force it to be used. Since the latest Nvidia drivers support the GLX_EXT_texture_from_pixmap extension, there's no need for either the AIGLX that ships in Edgy's X.org, nor GLX. AIGLX stands for Accelerated Indirect GLX, and as a technology, it was supported by the Nvidia drivers even before the AIGLX project came to being. 

> * Compiz and Beryl seem to be alternatives: what are the differences? Is there an impact on performace or what kind of applications work?Beryl is a recent fork of Compiz. Compiz is a bit more stable at the moment, and Beryl has a few added features and is more rapidly developed. There isn't a huge difference between the two, and most differences can be ported either way.
> * Xgl, AIGLX, using the drivers features directly seem to bee alternatives of how to get 3D and effects to work. What are the differences? What is the impact on running applications like
- 3D games in windows
- video players
- remote session viewersXGL gives you a separate X server, whereas AIGLX uses your existing one. Roughly speaking, AIGLX does better in all the aspects you mention, since it's built into your existing X server which should already be doing fine in them. XGL isn't likely to see much future use and support. I'd say resort to AIGLX whenever possible. See these for more info:

[http://jonsmirl.googlepages.com/graphics.html](http://jonsmirl.googlepages.com/graphics.html)
[http://principe.homelinux.net/](http://principe.homelinux.net/)
[http://en.wikipedia.org/wiki/Aiglx](http://en.wikipedia.org/wiki/Aiglx)
[http://en.wikipedia.org/wiki/XGL](http://en.wikipedia.org/wiki/XGL)

---

### Post by catanzag on 2006-11-22
This thread [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104) is a collection of guides and info docs about Beryl&Compiz. 
In particular, a link suggested there, [http://www.freesoftwaremagazine.com/node/1797](http://www.freesoftwaremagazine.com/node/1797) is an article explaining the differences between AIGLX and XGL. 
Also references in wikipedia articles shown by 23meg are clear.

regards

---

