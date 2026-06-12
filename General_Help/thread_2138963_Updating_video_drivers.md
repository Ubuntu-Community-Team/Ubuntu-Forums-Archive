---
title: "Updating video drivers"
date: 2013-04-25
forum: General Help
---

### Post by Dallas2coolio on 2013-04-25
Is there a way to update the video drivers so it's the same version as the one on Intel.com website? Since I think that would help the performance on games. I wonder if the default video driver is old on the Ubuntu. Since it seems like it detects the video card and runs it. But I wasn't able to find a way to find an updated driver like for Windows for Ubuntu. Where is the latest drivers I can get for Intel video cards for Ubuntu?

---

### Post by pqwoerituytrueiwoq on 2013-04-25
Latest stable:
[FONT=Courier New]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/FONT]
Latest unstable:
[FONT=Courier New]sudo apt-add-repository ppa:xorg-edgers/ppa[/FONT]

then run:
[FONT=courier new]sudo apt-get update;sudo apt-get upgrade[/FONT]

---

### Post by Sef on 2013-04-25
> [COLOR=#000000]Latest stable:[/COLOR]
[COLOR=#000000][FONT=Courier New]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/FONT][/COLOR]
[COLOR=#000000]Latest unstable:[/COLOR]
[COLOR=#000000][FONT=Courier New]sudo apt-add-repository ppa:xorg-edgers/ppa[/FONT][/COLOR]

[COLOR=#000000]then run:[/COLOR]
[COLOR=#000000][FONT=courier new]sudo apt-get update;sudo apt-get upgrade[/FONT][/COLOR]

You can copy and paste the commands, so no tying is necessary.

---

### Post by Dallas2coolio on 2013-04-25
Is it best to use the latest version? Is it stable enough to play games? Or should I just use the stable version?  Thanks

---

### Post by pqwoerituytrueiwoq on 2013-04-25
the unstable source can have bugs, crashes, etc. it is not recommend unless you know what you are doing 
they both should be good enough for gaming, depending on your hardware

---

### Post by Dallas2coolio on 2013-04-25
Well my Sony notebook has Intel HD first generation and my Gateway netbook has Intel GMA 950. Will the latest help games run better overall and get more FPS? Or will it also help some games that never ran will run on the latest?

---

### Post by Dallas2coolio on 2013-04-25
I know you say there are bugs but I just wonder if overall it will perform better for games since it's the latest. Kinda like Wine 1.5 works the best since it plays WoW and the stable 1.4 doesn't install the game since it hangs while it's trying to load setup.

---

### Post by snowpine on 2013-04-25
> **Dallas2coolio said:**
> Well my Sony notebook has Intel HD first generation and my Gateway netbook has Intel GMA 950. Will the latest help games run better overall and get more FPS? Or will it also help some games that never ran will run on the latest?

Each game has its own hardware requirements which you can read at the game's website. Can you name one or more of the specific games you want to play, so we can give you some concrete recommendations? :)

I don't know about your Sony notebook (please post the specs if you want assistance), but an Intel GMA950 netbook is terrible hardware for 3D gaming, absolutely terrible. There is no updated driver that can magically turn GMA950 into high-performance gaming hardware.

---

### Post by Dallas2coolio on 2013-04-25
Well the GMA 950 can get around 40 fps for WoW and can play Doom 3 at low settings when playing on Win XP Home but I just wanted to know that if the latest video driver for Ubuntu will perform the same as the latest one from Intel website. Basicly the latest one was made around 2009 for the GMA 950. The Intel HD drivers the latest one was just made last month or so so it's it newer but I don't know if Ubuntu has the same latest one and will perform the same as the Windows version. I just wanted to get the driver that gets the most FPS as possible. I play older games on the GMA 950 since it can't run the newer ones like Intel HD can.  All I wanted to know is that will the latest drivers get the most fps and also gets the most features out of any Intel video cards?

---

### Post by snowpine on 2013-04-26
pqwoerituytrueiwoq gave you great advice in post #2 if you want to test newer video drivers.

More info here (please read carefully): [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by 3rdalbum on 2013-04-26
I don't remember reading anything about performance improvements with the absolute latest Intel drivers. Best to just stick with what you have. If you really want to tweak, Intel has a driver installer available on their website.

---

