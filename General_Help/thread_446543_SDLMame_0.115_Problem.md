---
title: "SDLMame 0.115 Problem"
date: 2007-05-17
forum: General Help
---

### Post by Graham1 on 2007-05-17
Hi

I'm running SDLMame 0.115 on a 1.2 GHz laptop which I would have thought is capable of running somer (older) mame roms. However, on the statistics screen and the "ok to continue" screen, the system seems to lock up :(. Once I get through to running the game, the framerate is very low. 

I have installed Nvidia's driver (for desktop effects) and I'm thinking that maybe the OpenGL side of things is causing the slowdown. I read somewhere that OpenGL can be disabled (within mame.ini) but I'm not sure which commands to use. 

Anyone have any ideas?

:)

---

### Post by Graham1 on 2007-05-18
Bump.

:cool:

---

### Post by Dirkomatic on 2007-07-18
Are you by any chance running Beryl or Compiz?  I switch to Metacity Windows Manager before I using MAME and it works okay.  I would bet there is a way to use the mame.ini file to change the settings, but I don't know what they are.

---

### Post by shamael on 2007-08-18
Editing the mame.ini file is very easy. You should be able to find it in /etc/sdlmame/mame.ini.
Just open it with your favourite editor as root and look for the video options. The first setting is "video". The available options are "soft" or "opengl".
If you want to try both quickly you can switch in game with CTRL+F10.
Another way is through the command line: start your games with this syntax

```
 sdlmame -video <type> <name of game> 
```

Where "type" is either soft or opengl.


Also, try the open driver as well. I have an ATI card so I don't know much about Nvidia, but the mesa drivers worked much better than the binary ones in sdlmame.

---

