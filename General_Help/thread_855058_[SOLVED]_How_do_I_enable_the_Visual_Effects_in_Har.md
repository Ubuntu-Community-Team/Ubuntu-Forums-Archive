---
title: "[SOLVED] How do I enable the Visual Effects in Hardy?"
date: 2008-07-10
forum: General Help
---

### Post by ardchoille42 on 2008-07-10
I have been using Ubuntu since Hoary Hedgehog. Hardy Herron, like the previous releases is awesome - Ubuntu just keeps getting better.

```

$ lsb_release -a | grep Description
No LSB modules are available.
Description:	Ubuntu 8.04.1

```

I have recently installed (fresh install, I never "upgrade") Hardy Herron and am using an nVidia GeForce 6200 graphics card with the nvidia accelerated graphics driver installed and working:

```

$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce 6200/AGP/SSE2/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,

```

I've never used compiz or beryl but I am assuming compiz is installed (but not enabled) by default in Hardy. I clicked on System > Preferences > Appearance, went to the Visual Effects tab and clicked the radio button next to "Normal" in order to enable visual effects. What I am trying to do is install and use avant-window-navigator, and that requires a compositing manager. The problem is when I enable Visual Effects, the screen flickers and the window border disappears until I turn visual effects back off. It looks like Metacity is crashing but respawns when I turn the visual effects back off. My questions are:

1) Is this compiz or beryl?
2) How do I get it working properly so I can install and use avant-window-navigator?
3) What else do I need to install for compiz to work properly?

I've never used a composit manager in gnome before so I'm quite new to 3d effects.

---

### Post by uidb4056 on 2008-07-10
I hope this could help you [http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

---

### Post by angry_johnnie on 2008-07-10
> **ardchoille42 said:**
> 
1) Is this compiz or beryl?
2) How do I get it working properly so I can install and use avant-window-navigator?
3) What else do I need to install for compiz to work properly?


1. Neither... and both :-)  Beryl and Compiz merged into Compiz Fusion

2 & 3 It's actually turned on by default... if your computer can handle it, it will... otherwise, it really boils down to what kind of graphics card you have.  Nvidia cards are tricky.  ATI cards are even trickier.  Just get the appropriate driver, and you'll be able to use compiz.

If you only want AWN, however, compiz is not needed, since metacity can now be used as a compositing window manager.

press alt + f2 and then type **gconf-editor**

find **apps > metacity > general**

and check the box next to **compositing_manager**

then you'll be able to use AWN without having to use compiz.

---

### Post by ardchoille42 on 2008-07-10
> **uidb4056 said:**
> I hope this could help you [http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

Yes, that works, nice tutorial. However, the main problem is that when I enable compiz there is no titlebar at all.. it's completely missing.

What I need to know is how to get my titlebar back when compiz is enabled.

---

### Post by ardchoille42 on 2008-07-10
> **angry_johnnie said:**
> 1. Neither... and both :-)  Beryl and Compiz merged into Compiz Fusion

2 & 3 It's actually turned on by default... if your computer can handle it, it will... otherwise, it really boils down to what kind of graphics card you have.  Nvidia cards are tricky.  ATI cards are even trickier.  Just get the appropriate driver, and you'll be able to use compiz.

If you only want AWN, however, compiz is not needed, since metacity can now be used as a compositing window manager.

press alt + f2 and then type **gconf-editor**

find **apps > metacity > general**

and check the box next to **compositing_manager**

then you'll be able to use AWN without having to use compiz.

I've got compiz working and I like some of the effects. The problem is that when compiz is enabled, there is no titlebar - no way to move, close, minimize, or maximize windows unless I use the keyboard shortcuts. And, gnome-terminal doesn't work correctly without a titlebar.

Thanks, I didn't know Metacity can do compisiting now.

I'd really like to get my titlebar issue in compiz fixed, though, my system seems to be able to handle compiz just fine.. except for the missing titlebars.

---

### Post by angry_johnnie on 2008-07-10
> **ardchoille42 said:**
> 
What I need to know is how to get my titlebar back when compiz is enabled.

Maybe

**system > preferences > advanced desktop effects settings > window decoration**

Window decorations must be enabled in order to keep title bars.

---

### Post by ardchoille42 on 2008-07-10
Ok, apparently, with an nvidia card, there is a special command you have to run:

```

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

```

and then restart xorg to get the titlebars working again.

Everything is fixed and compiz is running nicely - with titlebars :)

Thank you folks for your assistance.

---

### Post by ardchoille42 on 2008-07-10
OMG! I now have avant-window-navigator working! This thing ROCKS!

---

