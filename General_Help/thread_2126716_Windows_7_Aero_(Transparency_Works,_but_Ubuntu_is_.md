---
title: "Windows 7 Aero (Transparency Works, but Ubuntu is stuck on Unity2D? )"
date: 2013-03-18
forum: General Help
---

### Post by Psil0cybin on 2013-03-18
Hey guys just a quick question if I am stuck using Unity2D, does that mean my laptop cannot support unity3d?
I can run windows 7 perfectly fine with the transparency and all, Im wondering if I need to update my Ubuntu Drivers?
What else could be causing this issue?

---

### Post by Moose on 2013-03-18
Wait up, so you mean that Unity3D refuses to run on your computer or something?

---

### Post by 3rdalbum on 2013-03-18
What graphics card have you got? You may need to install a driver to be able to use Unity 3d.

---

### Post by stinkeye on 2013-03-18
Post your output of the terminal command...
```
/usr/lib/nux/unity_support_test -p
```

eg 
```
[COLOR="#008000"]glen@Quantal:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVCF
OpenGL version string:  3.0 Mesa 9.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by Psil0cybin on 2013-03-18
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
Is my output

My computer is an Acer Aspire One i got a specific iso of Ubuntu to come with drivers for it.
It is not a popular computer, thus I think the drivers compiled with the ISO are not updated.

I tried using Compiz, that didnt work.
Running compiz --replace (made my computer crash, everything started flickering, it seems that it cannot handle that..maybe I did it wrong?)
No changes were made.
I think I should be able to run Unity3D, as Windows 7 is able to run with Aero and all special effects.

[B]Upgraded video card driver! Still got same results, stuck on 2D.
The upgrade I Did was the following.
"[/B]3D-accelerated proprietary graphics driver for Intel Cedarview cards.

This driver is required to fully utilise the 3D potential of some Intel Cedarview cards, as well as provide 2D acceleration of newer cards."
[B]It says it has 3D Support, but I don't seem to get it..
[/B]What I'm really trying to achieve, is to get the** top panel** to be **transparent**, everything else I can live with :)
When im using the launcher, It seems like the top panel is transparent, but I want it to always be like that.
I have been googling all night,I tried a number of tools, none that work. Its driving me nuts! 
but I really really appreciate the fast reply, and support guys

---

### Post by 3rdalbum on 2013-03-18
When you go to the login screen and press the cog icon, choose Unity and log in.

Also, is this copy of Ubuntu running directly on the computer, or through a virtualisation program? If the latter, you wont get 3D support.

---

### Post by Psil0cybin on 2013-03-18
Directly on the computer. But im confused why it says 
OpenGL vendor string vmware

---

### Post by stinkeye on 2013-03-18
I think that's because your falling back to the [**_[COLOR="#B22222"]llvmpipe driver[/COLOR]_**]("http://www.mesa3d.org/llvmpipe.html") to do
software rendering because of your GFX card and lack of availabe driver.
(llvm ...Low Level Virtual Machine)

What's your GFX....
```
lspci -k | grep -A3 VGA
```

My nvidia card will run fine using the open source nouveau drivers...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR]** lspci -k | grep -A3 VGA**
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
	Subsystem: Giga-byte Technology Device 351a
	Kernel driver in use: nouveau
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
```

---

