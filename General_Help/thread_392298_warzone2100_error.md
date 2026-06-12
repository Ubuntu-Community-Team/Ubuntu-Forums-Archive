---
title: "warzone2100 error"
date: 2007-03-24
forum: General Help
---

### Post by stonerrob420 on 2007-03-24
Hi! i installed warzone2100 on my Ubuntu Dapper system and I keep getting this error in terminal when I try to fire the game up. The package i used to install the game was the autopackage installer from [http://wz2100.net](http://wz2100.net)

rob@rob-desktop:~$ warzone2100
warzone2100: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libphysfs-1.0.so.1)

How do I fix it? Ive even tried downloading the rpm version and converting it with alien to deb but so far nothing works. :confused:

---

### Post by Redeyes_Gambit on 2007-03-24
Have you tried:

```

sudo apt-get install libc6

```

?

---

### Post by stonerrob420 on 2007-03-24
Hello! Already tried that this is what I get when I try to apt-get that file

rob@rob-desktop:~$ sudo apt-get libc6
Password:
E: Invalid operation libc6
rob@rob-desktop:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rob@rob-desktop:~$

It doesn't make sence that i already got the file but it wont work with warzone2100.:confused:

---

### Post by Redeyes_Gambit on 2007-03-24
Hmm... Quite puzzling. Let me try to get it to work on my end. I've installed warzone before and found it to be quite an enjoyable RTS. Maybe if we can get it working we could play a game or two sometime :D

---

### Post by Redeyes_Gambit on 2007-03-24
Well looky here! I found a nice .deb that works perfectly.

[http://download.gna.org/warzone/releases/2.0/warzone2100_2.0.5-0ubuntu1_i386.deb](http://download.gna.org/warzone/releases/2.0/warzone2100_2.0.5-0ubuntu1_i386.deb)

It's made for edgy so I'm not sure if it will work for you. If not we'll move to plan B.

---

### Post by stonerrob420 on 2007-03-25
I downloaded the file that you suggested and guess what? Error: Denpendency is not satfiable: libc6 I just dont understand why this wont work I had it installed once before and it worked great. But I'll keep looking for files.:)

---

### Post by Redeyes_Gambit on 2007-03-26
Hm. Very odd indeed. I'm guessing you have already tried un-installing and re-installing libc6? Do you have any older versions of libc installed?

---

### Post by stonerrob420 on 2007-03-26
I have tried many versions of libc is there any command that I can use in konsole like apt-get to be able to resolve the dependenices? It would be nice if the programmers would add a function that would automatically download dependenices for programs? I love linux wouldn't trade it for the world...really got tired of catching viruses and malware with Windozes XP Pro.
 once again here is the error >>>> rob@rob-desktop:~$ warzone2100
warzone2100: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libphysfs-1.0.so.1)
:)

---

### Post by stonerrob420 on 2007-03-27
This is kinda off in left field but here a error message when I try to startup llxdoom.
Its got the same problem but with a different libc6.

 rob@rob-desktop:~$ llxdoom
 Oct  7 2004                   Doom LEGACY v1.41                       23:35:59
DOOM Shareware Startup
Z_Init: Init zone memory allocation daemon.
system memory 503Mb free 36Mb
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
/usr/bin/llsndserv: relocation error: /usr/bin/llsndserv: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference:confused: 
musserver: unrecognized music entry (D_.)
open /dev/sequencer: No such file or directory
rob@rob-desktop:~$ 

wonder if the files are messed up? If so how do I know which one to uninstall? ubuntu if full of all kinds of libc_?.?-? files

All the other games and apps on the system work.[COLOR="Red"][/COLOR]

---

### Post by stonerrob420 on 2007-04-02
I'm taking a break off my problems with warzone2100 on my ubuntu computer and are on my XP winblows pro computer....I've been playing MS combat flight simulator trying to relax a little. Does anybody know an IP for a online Combat Flight server that I can fly on ? It's an old game but it's fun to play? If anybody wants to play let me know. :) :guitar:

---

### Post by stonerrob420 on 2007-06-01
If ya wanna play a game of warzone 2100 let me know and ill set it up.....I got it working! :p I'm running version 2.0.6 now

---

