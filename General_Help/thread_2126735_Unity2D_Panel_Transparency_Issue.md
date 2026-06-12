---
title: "Unity2D Panel Transparency Issue?"
date: 2013-03-18
forum: General Help
---

### Post by Psil0cybin on 2013-03-18
Im running Ubuntu 12.04, I have transparency working on windows 7, but for some reason Ubuntu doesnt want to allow me to use Unity3D.
I think the support for my graphic card is outdated using an Acer Aspire One D270 (Although I just updated from additional drivers, and it said I should have 3d support)

**Updated to: 
3D-accelerated proprietary graphics driver for Intel Cedarview cards.


This driver is required to fully utilise the 3D potential of some Intel Cedarview cards, as well as provide 2D acceleration of newer cards.


Unity2D is good enough for me, but I just want the top panel to be transparent. Using Compiz doesnt work(nothing shows up, crashes computer when using compiz --replace.
My output for Unity3D testing is.
Is there any solution to get Transparency on MetaCity for Unity2D?
```
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.4


Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       no

```

---

### Post by fantab on 2013-03-18
I have ASUS 1015CX, which has more less exact specs as Acer D270. I am using xfce (fedora) on it and xfce transparency works well. Compared to Ubuntu, Xubuntu will fare quite well on the netbook as it consumes very less system resources.

Intel Cedar View has very bad support for Linux.. there are a lots of issues with those graphics.. Compiz too is resouce hungry and that is probably why it crashes. If you like transparency then I suggest you give xubuntu a try.

---

### Post by c2tarun on 2013-03-18
Look the google+ link on [this]("http://www.omgubuntu.co.uk/2012/03/how-to-adjust-size-of-unity-2d-launcher-and-icons/") page. I think somewhere the guy mentioned how to edit the panel in 2D. I can't confirm because I am in office and G+ is blocked here.

---

### Post by Psil0cybin on 2013-03-18
I installed Xubuntu using sudo apt-get xubuntu-desktop 
Thanks!! I got the transparency to work, although
when I right click on desktop, it reacts faster with Unity? (there is a small delay?..Is this normal)
-Also is there anyway to set short cuts to to the terminal, like I got used to using CTRL+ALT+T
This is definitely an alternative, but is there anyway to get transparency on unity2d?
I just love the Gnome GUI

---

### Post by fantab on 2013-03-18
**c2tarun** has left a link in his post above. If you will read it you may get some pointers, hopefully in the right directions.

I don't know about the right click on destop issue.. perhaps its because its not a clean Xubuntu. You can, however, set the keyboard shortcuts to your liking. 

Actually Unity never worked on my netbook, for that matter none of *buntu did... In fact I was a bit surprised to read in your post that you are actually running Unity2D on your Acer.
I tried a few distros on my Asus Netbook, nothing fared as good as fedora_xfce.

---

### Post by Psil0cybin on 2013-03-18
> **fantab said:**
> **c2tarun** has left a link in his post above. If you will read it you may get some pointers, hopefully in the right directions.

I don't know about the right click on destop issue.. perhaps its because its not a clean Xubuntu. You can, however, set the keyboard shortcuts to your liking. 

Actually Unity never worked on my netbook, for that matter none of *buntu did... In fact I was a bit surprised to read in your post that you are actually running Unity2D on your Acer.
I tried a few distros on my Asus Netbook, nothing fared as good as fedora_xfce.

It was almost impossible to get Ubuntu or Any linux for that matter on my Acer!
but after alot alot and i mean ALOT of googling!
Apparently, someone made a ISO of 12.04 JUST for it!! with all the drivers!
I want to bow down to that person!
but thats how im here today.
I figured out all issues with xubuntu. 
Thanks wondering if i could get the transparency to work in unity though :(
maybe not i guess

---

### Post by Frogs Hair on 2013-03-18
I think you may be out of luck with 2D simply because you can't replace Metcity with Compiz in Unity 2D. Even the outdated Emerald theme manager requires Compiz.

---

### Post by c2tarun on 2013-03-18
> **Psil0cybin said:**
> I installed Xubuntu using sudo apt-get xubuntu-desktop 
Thanks!! I got the transparency to work, although
when I right click on desktop, it reacts faster with Unity? (there is a small delay?..Is this normal)
-Also is there anyway to set short cuts to to the terminal, like I got used to using CTRL+ALT+T
This is definitely an alternative, but is there anyway to get transparency on unity2d?
I just love the Gnome GUI

The delay you are experiencing on right clicking on desktop is normal in xubuntu-desktop. Few months ago when I was using Xubuntu then I felt this lag. Now I installed plain vanilla xfce4 on Ubuntu 12.04 (I know many people suggest its bad idea) and its working like a charm, very fast very responsive, I never felt my laptop so fast. Also my laptop is not heating much due to xfce4. But xubuntu-desktop is also good option, and you'll surely enjoy it. :)

---

