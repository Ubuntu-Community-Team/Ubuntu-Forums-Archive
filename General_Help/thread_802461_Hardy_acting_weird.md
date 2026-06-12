---
title: "Hardy acting weird"
date: 2008-05-21
forum: General Help
---

### Post by muschen on 2008-05-21
For some reason, hardy began acting very weird. It takes ages for the windows to show up, and even longer to switch workspace. I'm pretty new to linux, and I've no idea what's causing it. 

My first guess was Compiz, since the programs them selves work like they used too, it more the graphical, what can you call it? hmm, handling of the windows, like when switching workspace, browsing the menus and opening new applications (they did show up on the task bar, but not on the screen until 5-10 seconds later).
I've tried uninstalling compiz, which only send me back to the login screen when I tried to switch workspace and it was just as slow as before. So I reinstalled it, and now I'm back with the same slow system.

I also tried restarting the computer, and there was this message when shutting down, white text on black screen, before getting to the ubuntu shutting down thing, saying something, but disapeared before I could read it.

Help me, anyone? :(

---

### Post by pytheas22 on 2008-05-21
Instead of uninstalling compiz, try just turning it off: go to System>Preferences>Appearance and click on the Effects tab to disable it.  See if that helps.

If not, the next place to look is your graphics driver.  What kind of card do you have?

---

### Post by muschen on 2008-05-21
I tried it, and it works smooth again.
I think I have an: Intel Corporation Mobile 915GM/GMS/910GML


But I don't understand why it worked fine before, then.

---

### Post by pytheas22 on 2008-05-21
You mean it works fine without the desktop effects, or the problem is solved and everything works as it's supposed to?

---

### Post by muschen on 2008-05-21
It works fine without effects.

I have a suspicion I've messed with the driver in someway... But is there a way to reinstall it, or just reset it or something?

---

### Post by pytheas22 on 2008-05-21
You can reinstall the Intel video driver with:
```

sudo apt-get remove --purge xserver-xorg-video-intel
sudo apt-get install xserver-xorg-video-intel
```

but I'm not sure how much of a difference this would make.  I have a feeling that the problem lies with the compiz configuration, not the video driver itself--a way to test would be to try running something that requires video acceleration, like the game Tux Racer, which you can install with:

```
sudo apt-get install extremetuxracer
```

---

### Post by muschen on 2008-05-21
I tried reinstalling it, and then switching on effects, and it directed me back to the login screen.

Then I installed Tux Racer, and it works fine. Should I try switching compiz on now?

---

### Post by muschen on 2008-05-21
I tried unabling the different things in compiz, and for some reason the bicubic filter was messing with my laptop (: So now it all works again! Thank you!

---

