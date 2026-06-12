---
title: "Enemy Territory Problem"
date: 2004-11-04
forum: General Help
---

### Post by FX on 2004-11-04
I was running Warty and ET ran fine. I upgraded to Hoary and I had problems. The problems that I had would be a black screen would come up and thats all that would happen. I could move that black screen around with moving my curser. So I decided to go back to Warty thinking that Hoary might have broke it. Started working out just fine after the reinstall of Warty. Today I updated the system ( sorry can't remember what the updates where ) but no ET will not start up again and I have the same problem I had before.

I thought that maybe it was a 3d problem or maybe my card or the XFree config, but I downloaded and installed Tuxracer and that runs just fine.

Here is the last part of the output when trying to start ET in a term.

GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

Thanks ahead of time for any help.

FX

---

### Post by userX on 2004-11-04
I definitly looks like a video issue. What kind of video card are you using? If it's an Nvidia card check you /etc/X11/XF86Config-4 and make sure that you are using the "nvidia" driver and not the "nv" one, also, make sure that you uncomment "glx". Not exactly sure about Radeon cards, but make sure you're using a driver that would utilize your card.

Let me know,

Will

---

### Post by FX on 2004-11-04
Well not sure whats up, but this morning I started up ET again and it worked just fine. GLX was uncommented out also. I don't' know whats going on really. Only thing I can think of is maybe this laptop gets warm or hot and the vid will not work right. It is the Nvidia card and XFree is setup right witht he nVidia driver instead of nv.

Thanks for the reply though.

FX

---

### Post by userX on 2004-11-04
I was thinking about your comment, some laptops use cpu stepping to conserve power or maybe when they heat up. Where is will run slower under some circumstances, by upto about 50%. I'm wondering if this could be the case for you.

Will

---

