---
title: "Blender problems"
date: 2007-05-10
forum: General Help
---

### Post by scottpledger on 2007-05-10
When I go into blender (using 'blender -w') and I enter the game mode (by pressing 'p'), it will go into game mode just fine, the same when i exit game mode by pressing 'Esc'.  But if I try to enter into game mode again after that (again, by pressing 'p'), when I press 'Esc' to exit, it returns a Segmentation Fault and ends blender.  Any help would be very appreciated.

---

### Post by srt5 on 2007-05-10
Are you using the flgrx driver for ATI graphics cards by any chance? I get a segmentation fault whilst trying to enter game mode. Running under the console outputs 

```
srt5:~$ blender -w
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.4.
Checking for installed Python... got it!
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
Detected GL_ARB_texture_env_combine
Detected GL_ARB_texture_cube_map
Segmentation fault (core dumped)

```

I have installed Beryl on my laptop, and have configured my Xorg.conf file to use flgrx as the driver for my graphics. I've looked under apt-get and it is possible to install my missing driver by coding

```
sudo apt-get install xfree86-driver-fglrx
```

I'm not sure if this is any help with your problem, I just thought I'd point out that I'm having a similar problem when attempting to enter game mode. I don't consider myself to be an expert with blender by any means though, if nothing else this post will bump your problem up to the top ;)

---

### Post by scottpledger on 2007-05-10
> **srt5 said:**
> Are you using the flgrx driver for ATI graphics cards by any chance? I get a segmentation fault whilst trying to enter game mode. Running under the console outputs 

```
srt5:~$ blender -w
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.4.
Checking for installed Python... got it!
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
Detected GL_ARB_texture_env_combine
Detected GL_ARB_texture_cube_map
Segmentation fault (core dumped)

```I have installed Beryl on my laptop, and have configured my Xorg.conf file to use flgrx as the driver for my graphics. I've looked under apt-get and it is possible to install my missing driver by coding

```
sudo apt-get install xfree86-driver-fglrx
```I'm not sure if this is any help with your problem, I just thought I'd point out that I'm having a similar problem when attempting to enter game mode. I don't consider myself to be an expert with blender by any means though, if nothing else this post will bump your problem up to the top ;)

I'm using the original manufacturer/restricted nVidia drivers with a PNY Verto GeForce 7900 SE, Dual-Head with Xinerama.  I know that Xinerama messes with Beryl, so maybe it also screws up Blender??  I don't get any Xlib error, tho...  Again, any help would be appreciated.  I'm getting very frustrated with having to restart blender after every two tests on a game i'm making.

---

### Post by Daisybobs on 2008-02-14
I have this problem too, when you start blender in a terminal, does it say that it can't detect the sound card?

I have a hunch that this may be our problem.

Yes, I'm using an nvidia card too. And a soundblaster awe64 or something. I've tried disabling the sound with no success too. This bug happens with the ubuntu repo packages and the graphicall builds.

---

### Post by reed026 on 2008-02-20
```
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Segmentation fault (core dumped)

```

that is an output for me when running blender through terminal. 
I don't use flgrx drivers, as if not mistaken, they're not supported by Radeon 7000 VE.

---

