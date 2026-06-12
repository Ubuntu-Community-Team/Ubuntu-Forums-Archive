---
title: "3D Acceleration not working - Gutsy - ATI X1600"
date: 2007-11-09
forum: General Help
---

### Post by intimaAcE on 2007-11-09
Hey,

I've installed Gutsy and I'm really happy with it, only thing that's not working is some aspects of 3d  acceleration.

Compiz-fusion works fine with the desktop cube and all other effects, its just in any 3d FPS I've tried the textures appear corrupted. It occurs with desktop effects turned on and off, and when the game is running in fullscreen or windowed.

I've got composite turned off in my xorg.conf, if that makes a difference (I'm a linux newbie :P).

I'm using an ATI x1600 with the ATI binary driver (auto installed by gutsy restricted drivers manager)

Output of fglrx info is : 

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6473 (8.37.6)

```

Output of glxinfo | grep rendering is : (I suspect this is the problem, but I have no idea how to fix it)

```
glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

The games I've tried are Nexuiz and Open Arena, both have corrupted textures, but the actual geometry is fine. Oh and the text in Open Arena is also corrupted, but only once I enter a match. I would attach a screenshot, but I've no idea where the Nexuiz screenshots are saved.

Any help would really be appreciated.

---

### Post by garyj1972 on 2007-11-18
I have the exact same issue but with X1950.

 I have tried from a fresh Gutsy install:

Installing FPS 3D games without the restricted ATI drvier but only achieve 3 frames per second and found I'm unable to activate Compiz.

I've tried using ENVY to install the drivers and found the 3D games work fine, but the moment I install Compiz-Fusion The 3D games no longer work correctly.

I've tried installing GUTSY, GAME, COMPIZ, ATI DRIVER in every order possible to see if it makes any difference. In no configuration can I get both COMPIZ working and still play 3D games.

Any help that can be provided would be very useful. Bear in mid I'm only 2 weeks into Linux when it comes to recommendations.

Thanks in advance

Gary

---

### Post by garyj1972 on 2007-11-19
I thought I'd advise anyone facing a similar problem what I did to resolve this. It's not a perfect solution but it does allow me to do what I want.

On a fresh Gutsy i386 install with "GARY" as Admin user defined during install
Installed all hardware (wifi) in my case
Installed all Ubuntu updates
Installed ENVY  and ran it to update ATI driver
Installed Compiz Fusion Settings Manager from this link >   
       [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)
BUT DIDN'T ENABLE ANYTHING - JUST INSTALLED IT AT THIS STAGE

Now created a second Admin authorised user, for me called GAMER

Now in the original Admin account "GARY" for me I enabled the 3D cube, wobbly windows, etc... that I wanted.

These settings did not transfer to the "GAMER" account, so as long as I never enable Custom Effects on this account all my 3D games still run perfectly.

I appreciate this doesn't cure the proble but for me is a satisfactory work-around - hope it helps someone else. Gary

---

### Post by intimaAcE on 2007-11-19
Hmm, thanks for the tip but unfortunately that didn't work for me. Even on the second account I get "Direct rendering: no", even though the drivers seem to be installed fine.

This is really frustrating because all the games I try to play run at an unplayably low frame rate, or have texture/text corruption. Its like the drivers for the card are installed...but somehow its just not utilising the graphics card. 

If anyone has any idea how to solve this, pleeease post!

---

### Post by patryk77 on 2007-11-20
I'm having similar problems with my Radeon x1600 pro

Also running the ATI restricted binary drivers

```
$ LIBGL_DEBUG=verbose glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Radeon X1600 Series
```

I tried re-installing the drivers using a tool called Envy... It just changed my config to Mesa, and now everything is slow, and buggy

---

### Post by intimaAcE on 2007-11-21
> **patryk77 said:**
> I tried re-installing the drivers using a tool called Envy... It just changed my config to Mesa, and now everything is slow, and buggy

Yeah, I tried updating my drivers to the latest ATI release (which was a complete pain) and it changed my config to use mesa, even though I specified to use fglrx in xorg.conf. I ended up doing a complete reformat and starting from scratch, but this thread might be able to help you : 

[http://ubuntuforums.org/showpost.php?p=3547899&postcount=8](http://ubuntuforums.org/showpost.php?p=3547899&postcount=8)

Scroll (slowly :P) down to troubleshooting.

Still no clues to this direct rendering problem?

---

