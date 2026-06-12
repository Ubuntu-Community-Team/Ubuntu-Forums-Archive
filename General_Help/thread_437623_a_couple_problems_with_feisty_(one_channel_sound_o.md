---
title: "a couple problems with feisty (one channel sound only; compiz troubles)"
date: 2007-05-09
forum: General Help
---

### Post by allan.linux on 2007-05-09
Hello, All!  Ubuntu and Linux beginner here.  I have a few problems that have been buggin me for a bit.  I'm sorry if these have been mentioned before, but I've been scouring these forums for awhile now and I couldn't find anything similar enough to my problems.  This is my first time posting so if I screwed anything up by posting this please let me know.

First of all in my Ubuntu Feisty setup on my Dell Inspiron 6000 laptop, I only have sound coming out of the front left speaker.  Can't figure it out.  When I plug in a set of headphones, though, I get sound on both channels.  I don't know if that really makes a difference, but it feels like I should mention it.  When I do "asoundconf list" in terminal it says I have an ICH6 sound card.

Second, whenever I have GL Desktop enabled for compiz in an XGL session, the 3D acceleration and eye candy works fine, but sometimes when I hit Alt-tab it would get stuck and it just keeps "Alt-tabbing" for a few seconds.  A similar problem happens when I am scrolling in swiftfox - sometimes I would just tap the down arrow but instead of just scrolling down once it keeps on scrolling for a few seconds even when my finger has left the key.  It's like the corresponding key command gets "locked" sometimes, and it gets really annoying.  Turning off compiz fixes it, but that gets rid of the eye candy.

Finally, fullscreen video playback is choppy when compiz is on.  I've tried totem, mplayer, and VLC.  They all behave the same way.  Again, turning off compiz fixes it, but that defeats the purpose.  The video card is an ATI Mobility X300, or Radeon Mobility M300 which is what is shown when I do "lspci" in terminal.

I upgraded Feisty from Edgy fairly recently, but I honestly don't remember whether or not sound came out of both channels in Edgy.  I just recently configured compiz.

Any ideas?  Thank you for reading!

---

### Post by MyR on 2007-05-11
After a little bit of work Feisty works flawlessly for me on my inspiron 6000.

do both of your speakers work in any other os? it sounds like a hardware problem to me.

you can disable key repeats by system > preferences > keyboard then click accessibility and uncheck enable repeat keys

as for the video playback, you can configure mplayer and/or vlc to play using x11, this will likely fix the problem.

to configure mplayer:
right click somewhere on it to give you the menu then click preferences. under the video tab, change the driver to x11 (Ximage/Shm). hit ok and restart mplayer
to configure vlc:
settings > preferences > video > output modules > check advanced options > change video output to x11 > save

hope this helps

---

