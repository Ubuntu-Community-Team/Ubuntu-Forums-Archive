---
title: "Failed to start 'x server'? O_o"
date: 2007-01-09
forum: General Help
---

### Post by Scooter7 on 2007-01-09
Hi, I downloaded Ubuntu Edgy Eft, and burned it to a DVD-R.   I popped it in my drive, and turned on my PC.   First I checked the burn.   Ubuntu said it was okay.   So I chose 'Start or Install Ubuntu', and sat back and watched as a (rather pixelized) loading screen sat in front of me for a few seconds.   When the progress bar was done, the Ubuntu logo became even more pixelized, and a blue and green bar appeared on-screen.   Touching the arrow keys resulted in the bar changing form slightly.   So I restarted.   I changed the video mode to 1024x768 32 (what I use for Windows).   Ubuntu seemed to load up fine this time - at least past the initial progress bar, into a blank DOS-like interface, and then, after a few, I was presented with 'Failed to start X server (your graphical interface).   This could be because it was not set up properly.'   It also asked if I wanted to look at the configuration.   It makes no sense to me, and I can't remember what it said.   Any idea how to fix this?   Please keep in mind I'm a total newb when it comes to Linux, especially Ubuntu.

---

### Post by invalid on 2007-01-09
In a terminal (the DOS-like interface) type the following:
```
sudo dpkg-reconfigure xserver-xorg
```
When it asks you for a driver, choose a generic one (nv, or vesa).
This should get you started.

---

### Post by Scooter7 on 2007-01-09
Well, tried that, nothing happened when I hit ENTER except go down a line.

Actually I don't think the screen I saw was the Terminal.   It was just black with a single blinking cursor...

Any more suggestions?

---

### Post by vovo on 2007-01-12
This also seems to be happening to me too.

i have edgy written to a CDR, i have done all the integrity checks and everything was fine.
so when i reboot, i select boot from CD.
Then a screen pops up saying start or install ubuntu,
So i select that
Then the failed to start Xserver screen is displayed after a little while of waiting.
so i click NO to the question. it is disabled OK.

Then i get a black screen with a single white blinking cursor, i can type there but it seems to be more a word processor than a command prompt.

I just want try a live session of ubuntu before i install it but i don't get the option to do either.
I am new to this, and my level of experience is: Beginner

all help is appreciated
~vovo

---

### Post by Scooter7 on 2007-01-16
Alright, I managed to figure things out through a different thread, so, for vovo, and all others with this problem, here it is:

[http://www.ubuntuforums.org/showthread.php?t=328763](http://www.ubuntuforums.org/showthread.php?t=328763)

Please note that after you shut Ubuntu down the changes you make to get it working will be lost, unless you've installed Ubuntu.

Hope this helps,

   ~Scooter7 :cool:

---

