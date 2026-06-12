---
title: "Desktop Effects = White Screen"
date: 2008-06-20
forum: General Help
---

### Post by GOB1029 on 2008-06-20
Hello again,

I'm reinstalling Ubuntu Hardy amd64, and trying to get desktop effects enabled.  My graphics card is ATI Radeon x1250, I've downloaded and installed the latest Catalyst driver from ATI's website, as well as followed the setup guide found [here](http://forum.compiz-fusion.org/showthread.php?t=6794).

However, if I enable any desktop effects at all, the screen goes to a solid white (mouse still visible).  Or, if I reboot and login, I get the same white screen after seeing my desktop for about half a second.  I have to turn off desktop effects by setting metacity as the default window manager.

I'd really like to get desktop effects enabled properly, but I am a noob when it comes to things like this.  Any help would be appreciated, thanks!

---

### Post by pytheas22 on 2008-06-20
You could using envy to get the stuff set up.  I've seen it work a lot of magic for ATI cards even when a roomful of people with a lot of Linux experience couldn't get desktop effects working properly hacking by hand.  Plus someone in this [thread]("http://ubuntuforums.org/showthread.php?t=766984") says that for him or her, envy solved the same problem you're having with the same model of graphics card.

To install envy:
```

sudo apt-get install envyng envyng-gtk
```

and to run it:
```

sudo envyng-gtk
```

Then just follow the instructions and have it automatically configure your card.  It should do everything for you.

envy also has a go-back option so if it doesn't work, you can at least go back to the point you're at now.

Let us know if it helps.

---

### Post by GOB1029 on 2008-06-21
That worked magnificently!  Thanks so much.

However, I now have a new problem.  With compiz enabled, when I playback video, if it is windowed, it flashes, as in, it will display the video but constantly flashes to black.  If I fullscreen it (in totem movie player), it is fine, unless i move the mouse so that the "Leave Fullscreen" button as well as the time bar appear, it flashes black again.

The same type of thing happens when I rotate the desktop cube by hand  If there are windows open, when I rotate the cube, it flashes and flickers both black and white.  This is quite annoying as it sort-of ruins the "cool" look of it, and is especially bothersome for video playback.

Any ideas for that?

---

### Post by pytheas22 on 2008-06-21
Compiz still has some issues that haven't been worked out with video playback, so I suspect that's what's going on (you don't have the same problem with desktop effects disabled, right?).  But I've never seen anything as bad as you describe with black flashing in windowed mode.

What I'd suggest is that you try it in mplayer, another video player.  You can install mplayer with:
```

sudo apt-get install mplayer
```

and it will be put inside the Applications>Sound and Video menu.  See if the playback is still problematic in mplayer.  If it is, you can experiment with different video playback drivers to see if it makes a difference (I don't think this is possible in Totem, which is the reason I'm suggesting you try mplayer).  To change the video driver, right-click on the mplayer window and select Preferences.  Under the Video tab you can select which driver to use.  I've found that I have to select different options to get different kinds of video to play properly, although in general the xv driver works best.  I also have Intel video so my situation is different than yours.

---

### Post by pietjanjaap on 2008-06-22
> **GOB1029 said:**
> That worked magnificently!  Thanks so much.

However, I now have a new problem.  With compiz enabled, when I playback video, if it is windowed, it flashes, as in, it will display the video but constantly flashes to black.  If I fullscreen it (in totem movie player), it is fine, unless i move the mouse so that the "Leave Fullscreen" button as well as the time bar appear, it flashes black again.

The same type of thing happens when I rotate the desktop cube by hand  If there are windows open, when I rotate the cube, it flashes and flickers both black and white.  This is quite annoying as it sort-of ruins the "cool" look of it, and is especially bothersome for video playback.

Any ideas for that?

search on compiz and blue screen in players.(or compiz and video)
You have to change something in de players, because of compiz.
There is a website for that but i can't remember witch one.

---

