---
title: "Grey Screen Of Death After Watching Videos"
date: 2014-01-12
forum: General Help
---

### Post by carmen2012 on 2014-01-12
This doesn't happen all the time, but it does happen often enough that it is really frustrating.

On my pc, I will occasionally be watching a video in full screen mode.  When I press the escape key to get out of full screen, sometimes it doesn't work.  Instead, the entire screen will go grey or white.  The mouse arrow is on the screen and can be moved and I can also hear the audio from the video that was playing.  But, there is nothing else on the screen and the only way that I know how to get out of this situation is with a cold boot.

I am running Ubuntu 12.04 LTS on my laptop.

Has anyone come across this and know how to gix it?

Thank you

---

### Post by mörgæs on 2014-01-12
Which screen card do you use?

---

### Post by carmen2012 on 2014-01-12
> **mörgæs said:**
> Which screen card do you use?

Could you tell me how I could determine which screen card I am using?

I just installed Ubuntu and took all of the default settings.

---

### Post by mörgæs on 2014-01-12
Let's take the whole system.

Please run 
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by Impavidus on 2014-01-13
Instead of the cold boot, have you tried the [Magic SysRq key](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)? It may prevent collateral damage.

---

