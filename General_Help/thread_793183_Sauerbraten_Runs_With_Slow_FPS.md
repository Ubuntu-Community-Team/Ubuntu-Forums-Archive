---
title: "Sauerbraten Runs With Slow FPS"
date: 2008-05-13
forum: General Help
---

### Post by igfud on 2008-05-13
Hello,

I have a Gateway laptop which dual boots into both Ubuntu 8.04 and Windows XP.  I've installed the FPS game Sauerbraten on Windows.  It runs most maps at 30 frames per second or so, pretty smooth with no lags or other issues.

I decided to try and install Sauerbraten for Linux.  I downloaded the tarball, extracted it, and below is the terminal output when I tried to run it:

```
mike@igfud-laptop:~/Desktop/sauerbraten$ ./sauerbraten_unix
./bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

```

No problem; I read the directions [here]("http://ubuntuforums.org/showthread.php?t=266058") and installed the libSDL -dev package in Synaptic.  That didn't work, so I tried libsdl-image1.2 and libsdl-mixer1.2 per the latter post.  Sauerbraten started up fine, however the frame rate is quite slow (about 5-10 frames per second).  Is there anything I can do to speed it up?  It seems to be a rendering issue: if I stare at a wall it speeds up a bit, but runs much slower when there are many objects to render.

Below I've posted the terminal output when starting up the game:

```
mike@igfud-laptop:~/Desktop/sauerbraten$ ./sauerbraten_unix
Using home directory: /home/mike/.sauerbraten
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2 (Tungsten Graphics, Inc)
Driver: 1.3 Mesa 7.0.3-rc2
WARNING: No occlusion query support! (large maps may be SLOW)
WARNING: No shader support! Using fixed function fallback. (no fancy visuals for you)
WARNING: No framebuffer object support. (reflective water may be slow)
WARNING: Non-power-of-two textures not supported!
init: console
init: gl: effects
init: world
init: sound
init: cfg
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.1 seconds)

```

Desktop effects are not enabled.

Thanks!
igfud

---

### Post by mzembe on 2008-05-13
What is the output of: ```
glxinfo|grep render
```

---

### Post by igfud on 2008-05-13
```
mike@igfud-laptop:~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2

```

Edit: I have an integrated graphics chip.  It is an Intel 82852, I believe.

thanks,
igfud

---

### Post by igfud on 2008-05-14
I tried turning off many of the 'extra' options (pixel shading, water reflection, water refraction, turning the resolution down, etc.).  This seemed to speed it up a bit, as long as I was the only player on the map.  As soon as other players connect to the servers, the frame rate drops drastically and it is difficult to play.

After resetting the options, I was even able to obtain a 90 frames per second when staring at a wall.  Turn away and the rate drops to maybe 11 fps.

This is the only problem I seem to be having with Linux.  Everything else was worked perfectly out of the box!  I've been Windows free for several months now.

Any other ideas?  Maybe I should just stop gaming. :D

Thanks,
igfud

---

### Post by sdennie on 2008-05-14
Are you running compiz (Desktop Effects)?  You could try hitting Alt-F2 and then typing "metacity --replace" before starting your game and see if that helps.  (To restore compiz afterwards, hit Alt-F2 and type "compiz --replace").

---

### Post by igfud on 2008-05-15
Hello,

Thanks for the reply! I do have Desktop Effects disabled.  I played around with some of the options and was actually able to get it to run quite well, even on the heavily loaded servers.  Now I can play a really neat game, for free, and without Windows. :guitar:

igfud

---

### Post by puelocesar on 2008-06-12
> **igfud said:**
> Hello,

Thanks for the reply! I do have Desktop Effects disabled.  I played around with some of the options and was actually able to get it to run quite well, even on the heavily loaded servers.  Now I can play a really neat game, for free, and without Windows. :guitar:

igfud

Hi, I'm with the same problem, can you post what did you did to make it run well?

thanks

---

### Post by KNOTMIN3 on 2008-12-07
THANK YOU! igfud, you fixed my problem!

---

