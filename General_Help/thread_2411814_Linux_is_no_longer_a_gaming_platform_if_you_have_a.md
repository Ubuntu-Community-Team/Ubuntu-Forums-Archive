---
title: "Linux is no longer a gaming platform if you have a nvidia card :/"
date: 2019-02-04
forum: General Help
---

### Post by Notsgnik on 2019-02-04
Hi,
Since Ubuntu 18.04 I can't manage to play video games.
I get really low FPS where it wasn't the case with 16.04

I used official nvidia drivers ( 390 ) and also the ppa ones ( 415 ).

- I also added modeset 1 to sync screen.
- putted performance to max in nvidia setting.
- disabled [COLOR=#242729][FONT=Consolas]thermald, and [/FONT][/COLOR]irqbalance.

still no result.

Please Fix, it's the first time that I can't play native Linux games, on my linux machine, lot of people have the same problem and it's ruining the Ubuntu experience for any new comer.
So sad :'(

---

### Post by Autodave on 2019-02-04
How did you get 18.04: did you do a clean install or did you upgrade from an earlier version?

Can you give us some specs on your machine please?

---

### Post by CatKiller on 2019-02-04
> **Notsgnik said:**
> 
- I also added modeset 1 to sync screen.
That's not even close to what that does.

Your passive-aggressive tone suggests that you mistakenly believe that the volunteers here have anything to do with Ubuntu development, and mistakenly believe that the Ubuntu developers have anything to do with the proprietary Nvidia drivers, and that your own problems are somehow universal.

You might want to try again.

---

### Post by NM5TF on 2019-02-05
@Notsgnik...

post the output of

```
inxi -G
```

use code tags to make your response more readable....use [COLOR="#FF0000"]adv reply button[/COLOR], [COLOR="#FF0000"]#[/COLOR] to open code tags, paste reply between # characters..

[COLOR="#FF0000"][/COLOR]nvidia has dropped Linux support for many of it's older cards....nothing to do with Ubuntu or any other *nix distro....

have you tried using [COLOR="#FF0000"]nouveau[/COLOR] driver in place of nvidia driver ???

tommy

---

### Post by monkeybrain20122 on 2019-02-05
Probably the result of using gnome shell as default. If you google gnome shell slow fps you will find many threads, e.g [https://askubuntu.com/questions/907258/how-to-improve-fps-performance-in-gnome](https://askubuntu.com/questions/907258/how-to-improve-fps-performance-in-gnome) I find gnome shell in 18.04 laggy in addition to other inconvenience, so switched to unity.

---

### Post by monkeybrain20122 on 2019-02-05
> **NM5TF said:**
> @Notsgnik...


nvidia has dropped Linux support for many of it's older cards....nothing to do with Ubuntu or any other *nix distro....

have you tried using [COLOR=#FF0000]nouveau[/COLOR] driver in place of nvidia driver ???



I doubt it. If the card is not supported then he wouldn't have a desktop at all, not low fps. Besides, 16.04 and 18.04 use the same Nvidia driver for the same card and OP said it works on 16.04.

  Nouveau is crap for gaming.

---

### Post by Notsgnik on 2019-02-05
Hi, thanks everyone for your answers.

- modeset removed the teared screen and made it stable.

- yes it's a clean install, I even tried Mate desktop on the last Linux mint.

- the same driver worked perfectly on 16.04

- i've kabylake core i5 with an nvidia 950 gtx ( really common laptop actually )

- It's probably hard-drive related cause a 100 fish on fishgl.com demo works perfectly with no fps drops, yet when a fish is stuck it start lagging so maybe CPU :/

- inxi -G output:
> Graphics:  Card-1: Intel HD Graphics 620
           Card-2: NVIDIA GM107M [GeForce GTX 950M]
           Display Server: X.Org 1.19.6 drivers: i915,nvidia
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: GeForce GTX 950M/PCIe/SSE2
           version: 4.6.0 NVIDIA 415.27



- glmark2 :
> =======================================================
    glmark2 2014.03+git20150611.fa71af2d
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GTX 950M/PCIe/SSE2
    GL_VERSION:    4.6.0 NVIDIA 415.27
=======================================================
=======================================================
                                  glmark2 Score: 2626 
=======================================================


- "Unigne heven benchmark" is really slow when there is stuff moving on the screen ( 10 fps ) but fast with scenery full of detail ( 120 fps ).
 
Really looks like a CPU , File IO or Audio problem related problem

---

### Post by Notsgnik on 2019-02-05
Installed Opensuse, everything works :)

---

