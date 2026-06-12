---
title: "Color Depth?  How to change?"
date: 2004-11-13
forum: General Help
---

### Post by d0gbert on 2004-11-13
The color depth appears to set a tad too low on my install.  As a result, many backgrounds have "bands" instead of smooth gradient color transitions.  

Anyone seen this before?  My X11config-4 specifies the color depth is set at 24-bit.  Is there a tweek I can do to raise it up to 32-bit?

I have a Dell Inspiron 8100 notebook, which uses the Nvidia Geforce2 Go.  I see alot of people having trouble with the Nvidia drivers and thought I'd hold off...unless that is what is causing the "banding".  Otherwise, I can live without 3D enablement for a while.

Thanks!
d0gbert

---

### Post by TravisNewman on 2004-11-13
[QUOTE=d0gbert]The color depth appears to set a tad too low on my install.  As a result, many backgrounds have "bands" instead of smooth gradient color transitions.  

Anyone seen this before?  My X11config-4 specifies the color depth is set at 24-bit.  Is there a tweek I can do to raise it up to 32-bit?

I have a Dell Inspiron 8100 notebook, which uses the Nvidia Geforce2 Go.  I see alot of people having trouble with the Nvidia drivers and thought I'd hold off...unless that is what is causing the "banding".  Otherwise, I can live without 3D enablement for a while.

Thanks!
d0gbert[/QUOTE]
 24 it is the highest "true" depth. 32 bit is basically 24 bit with enhancements, which I thought were automatically applied (so says the Gentoo installation guide, so I don't have any hard and confirmed sources), but the issue may be the nvidia drivers. You can enable the universe repository in /etc/apt/sources.list and search for "nvidia" in synaptic and install the nvidia-kernel-common and nvidia-glx packages, then change "nv" in your XF86Config-4 to "nvidia," add nvidia to /etc/modules, reboot, and you should be good to go. I haven't seen MANY people with nvidia headaches here.

---

### Post by IoN_PuLse on 2004-11-14
24-bit is the same as windows in 32-bit mode, the extra 8-bits aren't use to enhance colours. (it is reserved for alpha channels I believe)

Anyways if you're seeing banding in images such as this: [http://www.ubuntuforums.org/screenshot/Screenshot.png](http://www.ubuntuforums.org/screenshot/Screenshot.png), it's because that image actually has banding. Of course that is just a screenshot but the actual background image has banding, which is strange...I proved it by opening it in the Gimp and gaussian blurring it like nuts made smooth gradiants out of the bands.

---

### Post by TravisNewman on 2004-11-14
[QUOTE=IoN_PuLse]24-bit is the same as windows in 32-bit mode, the extra 8-bits aren't use to enhance colours. (it is reserved for alpha channels I believe)

Anyways if you're seeing banding in images such as this: [http://www.ubuntuforums.org/screenshot/Screenshot.png](http://www.ubuntuforums.org/screenshot/Screenshot.png), it's because that image actually has banding. Of course that is just a screenshot but the actual background image has banding, which is strange...I proved it by opening it in the Gimp and gaussian blurring it like nuts made smooth gradiants out of the bands.[/QUOTE]
 Alpha channels! That's what the extra 8 are! Thanks, I was racking my brain over that.

---

### Post by d0gbert on 2004-11-14
ION_PULSE >> Yes, that image had about 15 or so "bands".  So, is there a way to turn  on the extra alpha channels?  It sure would make logon/desktop backgrounds much less distracting.  I was showing my girlfriend Ubuntu and her first comment was, "What's wrong with the desktop image?"

Does the type of video card installed have anything to do with this and whether or not the extra 8-bit alpha channels can be enabled?  

I'm wondering if installing the GeForce2 Go drivers on my notebook would "fix" this.

Thanks!
d0gbert

---

### Post by TravisNewman on 2004-11-14
[QUOTE=d0gbert]ION_PULSE >> Yes, that image had about 15 or so "bands".  So, is there a way to turn  on the extra alpha channels?  It sure would make logon/desktop backgrounds much less distracting.  I was showing my girlfriend Ubuntu and her first comment was, "What's wrong with the desktop image?"

Does the type of video card installed have anything to do with this and whether or not the extra 8-bit alpha channels can be enabled?  

I'm wondering if installing the GeForce2 Go drivers on my notebook would "fix" this.

Thanks!
d0gbert[/QUOTE]
 No, what he's saying is that a lot of images, like that one for example, have bands in them regardless of how high you set the depth. Are you saying that the default Ubuntu background was messed up? If so, was it just banding or what?

And you should most definitely install the nvidia drivers from synaptic.

---

### Post by d0gbert on 2004-11-14
PanickedThumb>> I see what you are saying.  Yes, the default desktop images was banded.  So, hypothetically, if someone were designing a desktop image, keeping the 24-bit color depth in mind, why wouldn't they adjust their image, like Ion_Pulse did in GIMP, so that it did not contain these bands?

I am in the process of installing the Nvidia drivers now.  I also am installing the configuration tool.  I'll post back here and let you know if it improves the image quality.

Thanks!
d0gbert

---

### Post by TravisNewman on 2004-11-14
Yeah ok. I DON'T think that the default desktop image should be banding like that.

Hopefully it's a matter of the drivers. I don't really know of any way to "enable" the other 8 channels really.

---

### Post by d0gbert on 2004-11-14
Sure enough!  No more color bands.  Desktop is now much nicer to look at.  
To summarize:  

- Used Synaptic to install 'nvidia-glx' and 'nvidia-settings'.
- Added 'nvidia' to /etc/modules
- In console typed 'sudo nvidia-glx-config enable'

The only strange thing I noticed is that the login screen text is now very large.  ?  Something with the resolution?  Does the order of /etc/modules make any difference?  I'll have to play around and see.

Thanks!
d0gbert

---

### Post by TravisNewman on 2004-11-14
[QUOTE=d0gbert]Sure enough!  No more color bands.  Desktop is now much nicer to look at.  
To summarize:  

- Used Synaptic to install 'nvidia-glx' and 'nvidia-settings'.
- Added 'nvidia' to /etc/modules
- In console typed 'sudo nvidia-glx-config enable'

The only strange thing I noticed is that the login screen text is now very large.  ?  Something with the resolution?  Does the order of /etc/modules make any difference?  I'll have to play around and see.

Thanks!
d0gbert[/QUOTE]
 No, the /etc/modules just tells it what to load at power-on, the order doesn't really matter unless a module depends on another one, but I've never had that issue. I noticed different GDM font sizes as well with different display drivers, and between XFree86 and xorg

---

