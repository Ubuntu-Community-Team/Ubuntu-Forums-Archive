---
title: "Problems with 3D graphics"
date: 2007-12-03
forum: General Help
---

### Post by Ozor Mox on 2007-12-03
I'm having problems with some applications that use 3D graphics, such as games. Some 3D game work fine (BZFlag, Alien Arena, Scorched 3D), others don't (AssaultCube, Urban Terror, TORCS). In the problem games, it seems the textures get mapped all wrong, or text does not display and instead only appears as white blocks. I've attached what happens in TORCS.

I assume this is to do with the fglrx driver that I have enabled, which also seems to disable my Ctrl+Alt+F1-F8 shortcuts. DIsabling it though uninstalls the driver and means that although the games display ok, they run at a painful framerate.

My graphics card is an ATI Radeon X800. Compiz-Fusion is disabled, it makes no difference either way.

Can anyone help? Anyone with my graphics card got these problems or solved them?

---

### Post by Ozor Mox on 2007-12-10
Bump. No one else has had this problem with the proprietary fglrx driver?

---

### Post by prahs rozar on 2007-12-13
I've been having similar problems too. Look in my topic when I post it as soon as possible.

---

### Post by Ozor Mox on 2008-01-10
A little bump because I am still having problems with almost every 3D game either having messed up graphics, crashing, or running like a dog. Just about the only ones that work fine are Scorched 3D and BZFlag.

All I know is that it's definitely related to the ATI proprietary driver because if I turn it off they all work fine, just with a very bad frame rate. I know I'm not the only one to have problems with this darned proprietary driver...is there some alternative I can install?

---

### Post by GoofusGreen on 2008-01-13
I have the same problem with linux games (OpenArena, Nexuiz, ioUrbanTerror, Bugsx, Sauerbraten, Tremulous, etc). Anything that isn't 3D like the HUD and menu text won't display. And only some models show up properly. However, CounterStrike 1.6 and Condition Zero on Wine function perfectly.

Btw, I'm running Gutsy on an Asus A8J with an ATI Mobility Radeon X1700 and fglrx.

---

### Post by erpo on 2008-01-13
In my experience, ATI cards do not work very well with Linux for 3D graphics. This could change since ATI is starting to get more open with their drivers, including 3D support, but writing new Free drivers will take time.

For now, pick up an nVidia card.

---

### Post by NineseveN on 2008-01-13
Try the fix posted here: [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

When I had my ATi card installed, I had to use that fix to run OpenGl games, otherwise, the textures were all messed up. It did not work for every game, and I have since installed a GeForce 7600, but it worked for some of the same manetioned in this thread.

---

### Post by FokkerCharlie on 2008-02-21
I'm having a very similar problem.

Running FlightGear v1.0 results in corrupted textures, while the CVS version runs more-or-less problem-free.  Torcs was also a problem.

I'm using the latest drivers (installed from here:  [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) )  on my laptop with Mobility Radeon 9600.

The FG devs advise that it looks like a driver problem.  Hope that AMD can fix it soon!

The thread above worked splendidly for me in terms of getting FG to run nice and quickly on my machine, but textures remain corrupt.

Cheers
Charlie

---

### Post by easy_target on 2008-07-06
Same problem here. The open source driver works ok but framerate is terrible. I can't play sauerbraten but apparently true combat:elite works fine. 
What is going on? Everything used to work fine in feisty...

---

