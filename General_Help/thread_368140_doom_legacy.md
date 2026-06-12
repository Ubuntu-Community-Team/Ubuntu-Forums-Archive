---
title: "doom legacy"
date: 2007-02-22
forum: General Help
---

### Post by stonerrob420 on 2007-02-22
Hello eveyone!:) I installed doom legacy out of the ubuntu repositories and it will not run. It boots up then crashes. This is the code i get : lsdldoom
 Oct  7 2004                   Doom LEGACY v1.41                       23:35:21
DOOM Shareware Startup
Z_Init: Init zone memory allocation daemon.
system memory 503Mb free 28Mb
20 megabytes requested for Z_Init.
W_Init: Init WADfiles.
Added file /usr/share/games/doom/doom1.wad (1264 lumps)
Added file /usr/share/games/doom/legacy.dat (80 lumps)
===========================================================================
                     This program is Free Software!
===========================================================================
I_StartupTimer...
I_StartupGraphics...
HU_Init: Setting up heads up display.
lsdldoom: symbol lookup error: lsdldoom: undefined symbol: open_music

How do I fix it?:confused:

---

### Post by lukew on 2007-03-05
> **stonerrob420 said:**
> Hello eveyone!:) I installed doom legacy out of the ubuntu repositories and it will not run. It boots up then crashes. This is the code i get : lsdldoom
 Oct  7 2004                   Doom LEGACY v1.41                       23:35:21
DOOM Shareware Startup
Z_Init: Init zone memory allocation daemon.
system memory 503Mb free 28Mb
20 megabytes requested for Z_Init.
W_Init: Init WADfiles.
Added file /usr/share/games/doom/doom1.wad (1264 lumps)
Added file /usr/share/games/doom/legacy.dat (80 lumps)
===========================================================================
                     This program is Free Software!
===========================================================================
I_StartupTimer...
I_StartupGraphics...
HU_Init: Setting up heads up display.
lsdldoom: symbol lookup error: lsdldoom: undefined symbol: open_music

How do I fix it?:confused:

I was looking for another problem which i am getting and I saw this. I hope it helps.

(In the thread there is mention to music )
[HTML]
http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/46969-installing-jdoom.html[/HTML]

---

### Post by GeryonD on 2007-03-05
Try with '--nosound --nomusic'.  You need to configure the music to work properly with timidity or another midi server program unless you have midi-hardware on your sound card which on-board sound cards do not have these days.  Infact, most new cards do not have any type of on board midi support anymore.

---

### Post by lukew on 2007-03-06
> **stonerrob420 said:**
> Hello eveyone!:) I installed doom legacy out of the ubuntu repositories and it will not run. It boots up then crashes. This is the code i get : lsdldoom
 Oct  7 2004                   Doom LEGACY v1.41                       23:35:21
DOOM Shareware Startup
Z_Init: Init zone memory allocation daemon.
system memory 503Mb free 28Mb
20 megabytes requested for Z_Init.
W_Init: Init WADfiles.
Added file /usr/share/games/doom/doom1.wad (1264 lumps)
Added file /usr/share/games/doom/legacy.dat (80 lumps)
===========================================================================
                     This program is Free Software!
===========================================================================
I_StartupTimer...
I_StartupGraphics...
HU_Init: Setting up heads up display.
lsdldoom: symbol lookup error: lsdldoom: undefined symbol: open_music

How do I fix it?:confused:

I could not get this one to work either. Ended up using lxdoom which works fine. Have not worked out how to turn on sound though.

Luke

---

### Post by lukew on 2007-03-06
You need to install lxdoom-sndserv.

If you still dont get sound try starting the application with

lxdoom-sndserv

---

### Post by stonerrob420 on 2007-03-06
Here is what i get with using the command llxdoom:

rob@rob-desktop:~$ llxdoom
 Oct  7 2004                   Doom LEGACY v1.41                       23:35:59
DOOM Shareware Startup
Z_Init: Init zone memory allocation daemon.
system memory 503Mb free 128Mb
20 megabytes requested for Z_Init.
W_Init: Init WADfiles.
Added file /usr/share/games/doom/doom1.wad (1264 lumps)
Added file /usr/share/games/doom/legacy.dat (80 lumps)
===========================================================================
                     This program is Free Software!
===========================================================================
I_StartupTimer...
I_StartupGraphics...
Using XFree86-VidModeExtension Version 2.2
Using MITSHM extension
Was able to kill my old shared memory
HU_Init: Setting up heads up display.
Starting music server [/usr/bin/musserver -t 20 -f -u 0 &]
/usr/bin/llsndserv: relocation error: /usr/bin/llsndserv: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
musserver: unrecognized music entry (D_.)
open /dev/sequencer: No such file or directory

this is what i get if i use lsdldoom:

 Oct  7 2004                   Doom LEGACY v1.41                       23:35:59
DOOM Shareware Startup
Z_Init: Init zone memory allocation daemon.
system memory 503Mb free 128Mb
20 megabytes requested for Z_Init.
W_Init: Init WADfiles.
Added file /usr/share/games/doom/doom1.wad (1264 lumps)
Added file /usr/share/games/doom/legacy.dat (80 lumps)
===========================================================================
                     This program is Free Software!
===========================================================================
I_StartupTimer...
I_StartupGraphics...
Using XFree86-VidModeExtension Version 2.2
Using MITSHM extension
Was able to kill my old shared memory
HU_Init: Setting up heads up display.
Starting music server [/usr/bin/musserver -t 20 -f -u 0 &]
/usr/bin/llsndserv: relocation error: /usr/bin/llsndserv: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
musserver: unrecognized music entry (D_.)
open /dev/sequencer: No such file or directory
rob@rob-desktop:~$ lsdldoom
 Oct  7 2004                   Doom LEGACY v1.41                       23:35:21
DOOM Shareware Startup
Z_Init: Init zone memory allocation daemon.
system memory 503Mb free 121Mb
20 megabytes requested for Z_Init.
W_Init: Init WADfiles.
Added file /usr/share/games/doom/doom1.wad (1264 lumps)
Added file /usr/share/games/doom/legacy.dat (80 lumps)
===========================================================================
                     This program is Free Software!
===========================================================================
I_StartupTimer...
I_StartupGraphics...
HU_Init: Setting up heads up display.
lsdldoom: symbol lookup error: lsdldoom: undefined symbol: open_music

seems that this appilcation is messed up:confused:

---

### Post by GeryonD on 2007-03-06
Like I mentioned before in my old post, start it with '--nomusic --nosound'.  The problem here is it was compiled against an older SDL mixer library.  A  function is being called that is not implemented in the new libraries included with Ubuntu.  There are a few ways around this, but probably not worth the trouble.  Download and re-compile lxdoom or grab the older SDL mixer library and put it in the directory lxdoom is in.

---

### Post by stonerrob420 on 2007-03-25
I finally just gave up and uninstalled the game wasnt worth all the trouble just to play doom. but thanks for the help everybody.

---

