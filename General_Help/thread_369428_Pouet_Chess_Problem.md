---
title: "Pouet Chess Problem"
date: 2007-02-24
forum: General Help
---

### Post by hellraiser_rob on 2007-02-24
Hi all, 

I'm having a few problems running the pouet chess app, basically after just a few moves (normally 3 moves).  Running it from the console spits out the following error:

```
rob@rimmer:~$ pouetChess
Xlib: unexpected async reply (sequence 0x89)!
```

My first thoughts were that the AI committed suicide when it realised how bad i am at chess, but then i thought it might be something else :)

If it helps, i'm running beryl

Cheers

Rob

---

### Post by nick.inspiron6400 on 2007-02-25
I had the same problem when i had beryl. I uninstalled beryl and it worked, i didn't like pouetchess anyway. 

Beryl was getting in the way of NetBeans.

Hope it helps,

Nick.

---

### Post by PetruM on 2007-05-15
Hi,

I'm having another problem:

```
petru@shoebox:~$ pouetChess
SDL_SetVideoMode failed : Couldn't find matching GLX visual
I try the window mode
SDL_SetVideoMode failed : Couldn't find matching GLX visual

```

Is my system missing anything? :???:

---

### Post by ndefontenay on 2007-05-15
My guess is that you are missing some GLX driver.
You should try to download and install them

(I'm not too sure about the package name though)

---

### Post by PetruM on 2007-05-15
I did **sudo apt-cache search glx** and installed some of those packages. I replaced the **nvidia-glx** package with **nvidia-legacy-glx**, but got the same errors, plus other. Then I switched back to the old driver (let's hope nothing bad happened :roll:). No luck so far.

Here's a paste of my **glxinfo** output, if anyone could help:

```
petru@shoebox:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
```

---

