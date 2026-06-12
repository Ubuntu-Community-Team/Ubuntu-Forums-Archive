---
title: "Fastest, smallest, bestest"
date: 2007-12-17
forum: General Help
---

### Post by peterpancreas on 2007-12-17
Hi everyone, I've got an old Thinkpad 600 that we use in the main room of the house for quick internet, e-mail and word processing.  I tried installing Xubuntu, Gutsy Gibbon, but it looked horrible, didn't like the wireless card (Linksys Wireless-G 802.11g), and was just all around a headache.

Does anyone have any recommendations for a tight, small build that I can plop on there that will optimize this old clunker for stuff like that?  And then maybe a nudge in the direction of the correct forum and zone for tightening up some of the bolts after its installed?

Thanks a lot in advance,
Stephan

---

### Post by ajmorris on 2007-12-17
have you tried the openbox or fluxbox window managers from the ubuntu repositories?

---

### Post by kerry_s on 2007-12-17
it always helps to post your specs.

DSL is really light, can be run in ram if you have enough.-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

puppy is another 1-> [http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

---

### Post by ajmorris on 2007-12-17
oh lol, sorry, you meant OSs, i thought you meant WMs :P

---

### Post by bodhi.zazen on 2007-12-17
Fluxbuntu is the smallest and fastest of the Ubuntus

If you find that too bloated, DSL is awesome, but a little light

You could look at Puppy Linux

---

### Post by yabbadabbadont on 2007-12-17
Or perhaps consider Wolvix.

---

### Post by peterpancreas on 2007-12-17
Thanks everyone, I'll start with those.

---

### Post by KCPokes on 2007-12-17
I'd go with Arch (with OpenBox).  Not the easiest install, but you get only what you want out of it.  Definitely the fastest OS that I've installed on my old 266MHz laptop.

---

### Post by josephcherng on 2007-12-17
I'll drop in another vote for FLUXBUNTU. it's beautiful and fast.

DSL - works fine but even for someone like me who still uses a CD WALKMAN, i find it a little to hurtful to the eyes, to put it mildly.

I use fluxbuntu on a Thinkpad 600e and it runs very fast. you NEED to tweak it a little to optimize performance but even on first install, it runs smoothly enough. there's really a wealth of information for the 600 as it's so widely owned but i find [www.thinkwiki.org](www.thinkwiki.org) to be the most comprehensive site.

Here's a list of things that work out of the box:
1. Display - native resolution
2. Audio - NO SOUND (but thinkwiki has the solution)
3. Wired Internet: works out of the box with my D-LINK ethernet PCMCIA card
4. Wireless: WORKS with my Linksys WPC11 V.3 but you need to unplug it before every boot-up or else the system locks up...i've tried the solution on ubuntu documentations but if you change the config.opts, thinkpad doesn't recognize the card anymore.
5. Hibernate/Standby: Hibernate WORKS fine. Standby basically just shuts of the screen and hard-drive but leaves the fan running.
6. Most of the Fn keys work.

Here are some things that i've done to optimize:
1. SPEED UP OS: changing the default depth to 16 in xorg.conf 
2. SPEED UP BOOT-UP: changing the resolution of the splash screen to 1024 x 768 in usplash.conf
3. SOUND: follow the steps from thinkwiki for the installation of ubuntu 7.04 on thinkpad 600e


I'm still trying to figure out how to set the clock though...anyone know how? or can anyone tell me how to do it through the terminal?

---

### Post by peterpancreas on 2007-12-18
Well, I reinstalled Xubuntu and got the wireless and display to work how I want (hooray!)- now my main goal is to optimize the system for my wimpy laptop specs (Release 7.10 Gutsy, Linux Kernel 2.6.22-14-generic, 281.4 MB mem, Pentium II Dechutes proc., 32 GB available space), and also trying to figure our how to get Abiword on the dang desktop.  I'm still getting used to the folder tree and am not really sure where all the programs are kept.

So if anyone can help me figure out how to optimize the system by, say, turning off unnecessary effects, etc, that would be RAD!

Thanks in advance!

---

