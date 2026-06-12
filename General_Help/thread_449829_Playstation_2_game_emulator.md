---
title: "Playstation 2 game emulator?"
date: 2007-05-20
forum: General Help
---

### Post by kdarkentity on 2007-05-20
Is there a ps2 emulator for ubuntu?

---

### Post by iAlta on 2007-05-20
ps2emu but it's not in development anymore...

but you know there's a better one called; PlayStation 2 Slimline

---

### Post by oskarloko on 2007-05-20
PCSX2

[http://www.pcsx2.net/](http://www.pcsx2.net/)

(and the newest version is for Linux !!! )

[http://ubuntuforums.org/showthread.php?t=399165](http://ubuntuforums.org/showthread.php?t=399165)

---

### Post by treblesix on 2007-05-23
HI,

I downloaded PSSX2 but am gaving probs getting it running on Feisty.
When it runs it complains about not being able to load GS plugin 'libZeroGSoglr.so.0.96.2: libCg.so'

The file in the directory though. Any ideas ?

---

### Post by darknightuk on 2007-05-23
think you have to have this installed [http://developer.nvidia.com/object/cg_toolkit.html](http://developer.nvidia.com/object/cg_toolkit.html)

---

### Post by kdarkentity on 2007-05-23
hey man i cant even get psx2 emu to run at all

---

### Post by treblesix on 2007-05-23
How do i install the stuff form that toolkit ?
There are just a couple of files in it and no documentation.

---

### Post by kdarkentity on 2007-05-23
i installed the files threw the terminal

---

### Post by treblesix on 2007-05-23
Where do u p put the files ?
In the emulator folder ?

---

### Post by kdarkentity on 2007-05-23
the files should be automatically installed to its own directory... i never found out what u do with the main emulator folder

---

### Post by treblesix on 2007-05-23
I noticed the toolbox files are already installed in the main folder.
I have tried the windows version as well, and couldn't get that to work either, lost cause i think.

---

### Post by kdarkentity on 2007-05-23
im actually tring to remove the files that i download to attepmt to get the emulator to work but i dont know where those files went

---

### Post by treblesix on 2007-05-24
The Nvidia files are already in the folder, so i am unsure why the error is showing :(

---

### Post by kdarkentity on 2007-05-25
what is the error you are getting?...and im pretty sure that Ubuntu doesen't run well with certain Nvidia cards

---

### Post by treblesix on 2007-05-26
The error is .......

Could not load GS Plugin 'plugins/libZeroGSoglr.so.0.96.2': libCg.so: cannot open shared object file. No such file or directory.

Even though both files are in the plug-in dir.

I have a Nvidia GeForce FX 5600 btw.

---

### Post by hikaricore on 2007-05-26
Check the output of:

> ls -la /usr/lib/libCg.so

ls -la /usr/local/lib/libCg.so

The error you're getting is not due to the plugin, but the library it's linked to.

You should get an output like this from one of those commands:

*-rwxr-xr-x 1 root root 3203977 2007-05-01 19:07 /usr/lib/libCg.so*

If not then you need to properly install the Nvida Toolkit.
Found here if you can't track it down: [http://developer.nvidia.com/object/cg_toolkit.html#downloads](http://developer.nvidia.com/object/cg_toolkit.html#downloads)

---

### Post by treblesix on 2007-05-26
Hi,

How do i install it "properly" ?

There are 2 files in the toolkit, but no installer.

---------EDIT

I have found this and installed it, and the emulator gets to the main screen now :)

[http://packages.debian.org/unstable/libs/nvidia-cg-toolkit](http://packages.debian.org/unstable/libs/nvidia-cg-toolkit)

---

### Post by Nanoboy on 2007-05-26
hey treblesix,

Are you using PCSX2 or PSSX2 emulator?

I'm quite tempted to give it a try - never used a game emulator before in my whole life!  Am pretty new to Ubuntu but am loving it!!  ;)

---

### Post by treblesix on 2007-05-27
I am using PCSX2 for PS2 emulation.


I have PCSX installed, which I have sort of got Final Fantasy 9 working on, but it crashed and seemed a bit slow in parts.


I have got PCSX2 to get to the main menu screen, but can't seem to do much else with it at the mo, but will keep trying. I need an option to just insert a PS2 disc and load off it, but cant find an option for that.

I cant seem to make ISO's from my PS or PS2 disks either.

-EDIT

There are aload of emulators available in the Ubuntu repositories..............
**KxMame** - Arcade machine emulator
**Scumm **- LucusArts old game engine (like Day Of The Tenticle)
**UAE** - Amiga emulator

I have got those 3 working well.

You can also look into using **WINE**, if you want to run some Windows games. I have got StarCraft working great through it.

---

