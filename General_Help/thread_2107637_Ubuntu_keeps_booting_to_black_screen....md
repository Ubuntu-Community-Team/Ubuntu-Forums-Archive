---
title: "Ubuntu keeps booting to black screen..."
date: 2013-01-22
forum: General Help
---

### Post by smitty4478 on 2013-01-22
My Ubuntu won't boot it just goes to a black screen with the cursor (not frozen). I can access the root menu and stuff and it wont boot in failsafe mode, I'm a Linux noob so please help. And I'm using the newest Quantal Quetzal.

---

### Post by bogan on 2013-01-22
Hi!, **smityy447**8,

Check out the MAFoElffen Sticky in the Installations & Upgrade Forum: there is a step-by-step troubleshooter in Post#1, and an index in Post#2.
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)

Are you trying to boot from a new installation, or can you boot correctly from a LiveCD/USB ??

If you need more instructions please Post: ```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan.**

---

### Post by smitty4478 on 2013-01-22
It's a recent installation (about 2 weeks ago) but I haven't had this problem before. I don't know if it makes any difference but sometimes when I would boot up Ubuntu it would go to a purple screen and if I restart it would boot up properly. 

And It is a 64-bit installation, dual boot with Windows 7, AMD graphics and processors (read about Nvidia driver problems so it can't be that, right?).

---

### Post by bogan on 2013-01-23
Hi!, **smitty4478,**

Some AMD cards are affected by some of the same issues as nvidia cards, so it may or it may not,

Please post the requested data.

Chao!,** bogan.**

---

### Post by smitty4478 on 2013-01-23
So do I input that code into the Root and then tell you the output?

---

### Post by grahammechanical on 2013-01-23
When we run the Ubuntu live session we use the open source Nouveau video driver. When we install Ubuntu and check/tick install third party software the installation process installs a proprietary video driver.

I do some testing of ISO images and I always install without ticking Third Party Software so that I get the Nouveau driver and usually a working desktop. We can install the Restricted packages after installation and also activate a proprietary driver afterwards as well.

If you can get to a desktop you can try changing video drivers from System Settings>Software Sources - Additonal Drivers tab. See, if that improves things.

To get to a desktop you can do a couple of things.

1) Open the Advance Options sub-menu and select an earlier kernel to boot.
2) Open the Advance Options sub-menu and select Recovery Mode.

At the Recovery Mode menu select Resume. That sometimes works because it loads Ubuntu without activating a video driver. So, we use Nouveau instead.

3) At the Grub menu with Ubuntu selected press E. That puts Grub into Edit Mode. Now look for the line that has quiet splash in it and change it to

> nomodeset quiet splash

That will load Ubuntu without setting a video mode. That sometimes gets us to a desktop. Press F10 to boot.

If you remove quiet splash you will see messages and may see a message that gives information about what is failing to load.

Regards.

---

### Post by bogan on 2013-01-23
> **smitty4478 said:**
> So do I input that code into the Root and then tell you the output?Open a terminal, [Ctrl+Alt+t] or a text terminal[Ctrl+Alt+F1] and copy paste the commands one at a time to the terminal prompt.

Then copy/paste the output back into a New Reply edit box of the browser, highlight it and press the '#' Icon in the toolbar at the top of the box, to place it in code tabs to make it easier to read.

If you have a three button or a scrollwheel mouse, copy/paste is easy: highlight the line move the mouse cursor to the terminal cursor position or other destination, and press the scrollwheel/middle button. Similarly in reverse.

Otherwise 'Ctrl+c' copies & 'Ctrl+v' pastes, but in a terminal you need to use: 'Shift +Ctrl+c or v', or you can use the edit menu.

[ If you use the 'Ctrl+Alt+F1' route you may need to use:'Ctrl+Alt+F7 afterwards, to get back to the GUI. Actually, you do not want to use that way in this case, but for other commands you may need to].

Chao!, **bogan.**

---

### Post by smitty4478 on 2013-01-23
> **bogan said:**
> 
If you need more instructions please Post: ```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```

```
 lspci -nnk | grep -iA3 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6520G] [1002:9647]
	Subsystem: Hewlett-Packard Company Device [103c:3564]
	Kernel modules: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string:  2.1 Mesa 9.0

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

This is what I got back.

---

### Post by bogan on 2013-01-24
Hi!, **smitty447**8,

Have you tried **grahammechanical**'s suggestions in Post#6 ??

And the Trouble Shooter in the Installations & Updates Blank Screen Sticky ??

If so, what results ???

Chao!,** bogan.**

---

### Post by smitty4478 on 2013-01-25
I just loaded a previous kernel then hit resume and it booted fine then I updated and it works perfect now, thanks for all your help everyone I truly appreciate it! :)

---

### Post by bogan on 2013-01-26
HI1, **smitty4478,**

Great, glad you got it sorted.

You Posted;>  I updated and it works perfect now, To help some of the many others who catch the 'Black Screen Plague', please Post details of what you updated.

The kernal, the video driver or what ? and from which  to what version, and which video driver are you now using?

Chao!, **bogan**.

---

