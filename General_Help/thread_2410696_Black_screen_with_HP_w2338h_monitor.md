---
title: "Black screen with HP w2338h monitor"
date: 2019-01-19
forum: General Help
---

### Post by mrl3734 on 2019-01-19
I just pulled my old System 76 desktop out of storage (was sitting there for over a year) and was trying to set it up. Everything was going swimmingly until I tried to upgrade to 18.04. I am using a HP w2338h monitor with a VGA cable connected through a VGA<>DVI adapter. After the upgrade I got a message along the lines of "The screen locker is broken, hit ctrl-alt-F2 to go to terminal, type loginctl unlock-sessions, then ctrl-alt-F7 to go back". 

Except...I can't see anything in terminal mode. I hit ctrl-alt-F2, couldn't see anything, then went back to F7, where I saw the message, then held down the CPU power to hard shutdown and then start back up. And then...nothing. The monitor doesn't want to recognize any input that isn't graphical, seemingly, so I can't see a basic non-graphical command prompt terminal or get into the BIOS. It's just...a black screen with an amber (not blue) light on the monitor's power button. I can tell that the computer is starting up on some level, but I can't see what it's doing.

So I'm stuck here with a black screen. I'm sure I could figure this out if only I could SEE ANYTHING. What are my options? Try the HDMI input on the monitor? Get a new monitor? Forget about Ubuntu entirely and become a hermit? This had been a reliable desktop for a while, but I'm confused as to why I have so many problems with something so basic as having the monitor stay in sleep mode when the computer is in a non-graphical state. Any help? Please?

---

### Post by mrl3734 on 2019-01-19
Fixed it.

The monitor wasn't properly recognizing a signal coming over the VGA<>DVI-A connection. Using HDMI<>DVI-I worked. Past that point I learned that a kernel panic was causing the boot to freeze up, so I changed kernels and ran in recovery mode. A little bit of dpkg/apt-get action later and everything is okay now.

---

