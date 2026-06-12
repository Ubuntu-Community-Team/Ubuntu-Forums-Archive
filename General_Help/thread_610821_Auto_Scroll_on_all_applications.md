---
title: "Auto Scroll on all applications"
date: 2007-11-12
forum: General Help
---

### Post by smergs on 2007-11-12
First off let me say I am a n00b.   This isn't the first time I've tried out Ubuntu, but I would say the first time I've wanted to seriously use it.

I have installed 7.10 on an old Dell laptop that I have.  P3 500 mhz 512 mb ram 8mb video card. (really really old laptop)

Before I explain, I also wanted to say that I'm not sure if this is supposed to be a feature that just needs to be disabled or if it is just a strange issue.

My issue is that when I move the mouse cursor (using a touch pad) around the screen in firefox or in open office, I have found that the application automatically starts to scroll down in the window (when I move the mouse down).  I'm going to have to check back after work today, but I don't think it scrolls up this way.  Only down.  I need to get it to stop doing that!!!  It's been a bit of an annoyance for me, but not a deal breaker on using Ubuntu.  However, my wife likes using this old laptop for doing school work (she's a teacher) and when she noticed this happening last night it about drove her crazy.  She insisted that I reinstall Windows.  I'd personally would prefer to stick with Ubuntu, but unless I find a fix for this I may have to go back to windows.

Thanks for any help anyone can give me!!!

---

### Post by smergs on 2007-11-12
Bump.

---

### Post by smergs on 2007-11-12
Anyone?

---

### Post by smergs on 2007-11-12
up.

---

### Post by smergs on 2007-11-12
I think maybe I found something after a couple of times rewording my google search.


Due to the location and sensitivity of the touchpad, I find it necessary to turn off tapping and scrolling:

  apt-get install gsynaptics
  Added 'Option "SHMConfig" "true"' to the "Synaptics Touchpad" section of
    /etc/X11/xorg.conf and logged back in.
  System >> Preferences >> Touchpad:
    Disabled tapping and scrolling.
    Adjusted the sensitivity very slightly or else it gets set to zero on the
      next login.

Again I'm new to Ubuntu and really Linux all together so I don't know if this is going to work or not.  I found this information @ [http://jjinux.blogspot.com/2007/10/linux-ubuntu-710-on-compaq-presario.html](http://jjinux.blogspot.com/2007/10/linux-ubuntu-710-on-compaq-presario.html)
I guess since I haven't had any replies here that's what I'll try tonight.  But if anyone has any other suggestions or feedback, please let me know.   Thanks!

---

