---
title: "Doom Legacy sound error"
date: 2005-10-31
forum: General Help
---

### Post by bison on 2005-10-31
I get the following error running Doom Legacy:

<pre>
bison@bison:~ $ lsdldoom
 Oct  7 2004                   Doom LEGACY v1.41                       23:35:21
DOOM Shareware Startup
Z_Init: Init zone memory allocation daemon.
system memory 1011Mb free 137Mb
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
bison@bison:~ $
</pre>

I have doom-wad-shareware, doomlegacy-data, doomlegacy-sdl, libsdl-mixer1.2, and doomlegacy-x11 installed.  I am using an Ensoniq ES1371 sound card, which works otherwise.

Any ideas?

---

### Post by Gaming_Junkie on 2005-10-31
Did you try running "killall esd" as root before playing the game?

A few days ago I couldn't get sound in most of my games, and that fixed the problem.  Although I still can't get UT 2004 to have sound...

Also, after you finish your game, if you don't hear any sounds, run "esd" as root, that should fix it.

---

### Post by bison on 2005-11-01
[QUOTE=Gaming_Junkie]Did you try running "killall esd" as root before playing the game?[/QUOTE]

I gave this a try, but I have the same problem.  I also tried running lsdldoom as root, but that didn't work either.

Since the sound card works with everything else, I'm wondering if there isn't something wrong with one of the lsdldoom packages.

---

### Post by giacomolg on 2006-09-17
exactly the same error here...
(tried *killall esd* as well)

:-(](*,)

---

### Post by drseuk on 2006-11-06
Same problem on a Thinkpad T20 with a Cirrus Logic (Crystal fusion soundcard). Most likely a problem with lsdldoom itself.

> **giacomolg said:**
> exactly the same error here...
(tried *killall esd* as well)

:-(](*,)

---

### Post by Takmadeus on 2007-03-03
I get the same error.... tried with -nomusic, but it messed up the X server.... had to restart it... any ideas?

---

