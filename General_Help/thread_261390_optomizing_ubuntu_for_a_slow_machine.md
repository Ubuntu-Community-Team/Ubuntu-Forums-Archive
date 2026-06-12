---
title: "optomizing ubuntu for a slow machine"
date: 2006-09-20
forum: General Help
---

### Post by el_ricardo on 2006-09-20
I have xubuntu dapper installed on qute an old PC, this is a 700MHz celeron, with a geforce MX440 PCI graphics card (with nvidia GLX drivers installed) 320MB SDRAM, with 815MB additional swap space (i also tried to set up a very old 810MB hard disk to be used soley for swap but it doesn't seem to work!) I don't even know the motherboard spec, but its OLD! I installed xubuntu as opposed to the standard ubuntu of kubuntu with the idea in mind that this would run more efficiently on an old machine. It does run ok, but it still takes a while to load certain apps, and the CPU useage seems eratic when performing relatvely simple tasks. So could anyone give me any tips for making this install fully worth while?

cheers!

---

### Post by tatimmer on 2006-09-20
I run ubuntu on a 350 Mhz Pentium II and dual boot with win98.  

Starting openoffice writer takes about 15-20 sec.  Nautilus starts up in about 5-10 sec.  MSWOrd and WindowsExplorer start up almost immediately on win98.

I guess the slower startup on linux may be because:

1) the ways the apps are written, number of dynamic librarys to link ...

2) the client/server nature of X-windows.  my command line apps are as fast or faster on linux. Also having window managers and gnome/kde layered on top of X may slow things down a bit compared to an integrated window system.  

Personally Im happy with ubuntu. Sure it would be nice if all apps started immediately on my machine. Its good to slow down a bit in our fast paced world.

---

### Post by el_ricardo on 2006-09-20
[quote="tatimmer"]Its good to slow down a bit in our fast paced world.[/quote]

agreed!

....I'd still like things a *bit* faster though, i'd like to be able to watch a dvd for example without jittery video

---

### Post by ferebee on 2006-09-21
> **el_ricardo said:**
> 

....I'd still like things a *bit* faster though, i'd like to be able to watch a dvd for example without jittery video

You may have to try out different video drivers in the settings
dialog of your chosen player before you find the one best suited to your computer.

Also, according to [this]("https://help.ubuntu.com/community/DMA") link DMA
is automatically enabled in Dapper, but you could check it out.

I'm using Ubuntu on a 600mhz PIII, and while it's not a speed demon, things work well. (Faster than with XP anyway :))

---

