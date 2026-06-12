---
title: "Full Screen Game Resolution issue"
date: 2008-04-14
forum: General Help
---

### Post by pslim940 on 2008-04-14
This isn't a major problem, but it is something that has been bugging me for a little while.  I've done quite a bit of googling and still haven't found a solution.  

Running Gutsy now (had the same problem with Debian Lenny), I use a 1280x1024 resolution at 24 bit colour and all is fine, unless a full screen game is played, most notably my daughter playing Planet Penguin Racer(or any 3d game).  The game plays fine, but when exiting, the resolution has changed to 1024x768(or on occasion exits to a blank screen).  The resolution can than be changed back to 1280x1024 manually, but I would prefer to eliminate this step.  

The computer is a Dell Dimension 2350 with 512 mb RAM with integrated intel graphics. I have used the "Screens and Graphics" tool to select my monitor as well as use the right driver, but still get the same problem.  I'm at work now so I can't post my Xorg.conf file, but any help would be greatly appreciated.

Thanks.

---

### Post by GCoffee on 2008-04-14
It sounds like there is a line in the gaming code that sets the screen resoloution. Not strictly related but when I used fedora 8 any application that ran fullscreen on exit froze the whole computer.

Do you know if the resoloution changes when the game starts at all? If so it could mean ubuntu judging your resoloution wrong.

---

### Post by pslim940 on 2008-04-14
> **GCoffee said:**
> It sounds like there is a line in the gaming code that sets the screen resoloution. Not strictly related but when I used fedora 8 any application that ran fullscreen on exit froze the whole computer.

Do you know if the resoloution changes when the game starts at all? If so it could mean ubuntu judging your resoloution wrong.

Well, I know that Planet Penguin Racer plays at 800x600 usually, I've also tried increasing it to 1024x768 and still get the same problem.  I've also tried increasing it as high as 1280x1024, but then the game is too slow and choppy to play.  I know in Feisty I left the game at fullscreen, 800x600, and when it was exited, the resolution reverted back to 1280x1024 on my desktop.

---

### Post by cometa2k7 on 2008-04-15
I get a similar problem when I run games.

I use 1152x864 on my computer, but when I play a game, or open any other fullscreen app, other than GIMP, the resolution reverts to 1024x768.

I'll post my xorg.conf here
> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"DELL E772p"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


EDIT:
If I set the resolution to 1152x864 again, before opening the game, even though it's not changing the resolution, it seems to keep 1152x864 when I exit the game.

Is there any script that I can set to run on start up to do this for me?

---

