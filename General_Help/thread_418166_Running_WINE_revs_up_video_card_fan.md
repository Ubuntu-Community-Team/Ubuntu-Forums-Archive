---
title: "Running WINE revs up video card fan?"
date: 2007-04-22
forum: General Help
---

### Post by vertigo1980 on 2007-04-22
hi all,

i am running an updated feisty and updated wine, and every time i run winecfg or an app with wine (even a cli exe file, so no interface needs to be drawn), the fan on my graphics card revs up as if i was playing a video or just started up beryl. anyone else experiencing this? i don't like my card revving up for nothing, and it can't be good considering how many times i run wine.

running latest nvidia proprietary drivers, 9755 and a geforce 7900. the same happened with the previous 'stable' drivers. i am still new to linux but i remember the same happened on edgy too.

thanks! :)

---

### Post by vertigo1980 on 2007-04-23
...anyone?

---

### Post by uberNoobZA on 2007-04-23
Hi. I'm not sure how WINE interfaces with the graphics card and/or drivers, but I assume that WINE would startup some sort of DirectX compatibility when it runs. This is most likely what is causing the fan to speed up on your graphics card. Try and find a way of monitoring your GFX card temperature with and without WINE running.

This however MAY be a driver issue, as I experience the same thing when I launch NVidia Control Panel on my Windows XP install. The fans slow down again after a few minutes.

---

### Post by Elle Stone on 2007-12-31
I'm running Gutsy Gibbon 64-bit with amd opteron processor on a tyan thunder mainboard, (relatively fresh install - just switched from windows to ubuntu).  My graphics card is a nvidia 7600gt with the latest driver.  I have the exact same problem as Vertigo1980.

When I boot the computer, the gpu fan runs constantly until I "startx" to my icewm desktop (I don't use any of the *dms).  I don't run any 3-d graphics programs under wine (or native) and my desktop is pretty plain.  

I seem to recall, but could easily be wrong, that the gpu fan ran constantly until I installed the proprietary nvidia driver.  But as I installed said driver almost immediately upon getting a desktop up and running, it could be that the fan just hadn't had a chance to shut down.

So perhaps the problem is that wine itself doesn't actually use the nvidia driver, and the nvidia driver is what is needed to slow the fan down sooner rather than later?  I don't know how to research this issue further - any research suggestions or even solutions! are very welcome. 

The gpu fan does run even without wine being started up.  It just runs slower and so makes no noticeable noise unless I take the cover off and stand close to the computer.  I had to take the cover off to figure out what was actually making the noise when wine starts up.  That is when I realized that when the noise finally stops, the fan is still going, just not as fast.

Thanks in advance if anyone has any pointers to a solution or to how wine handles graphics cards.

Elle

---

### Post by pointone on 2007-12-31
May be related to [this]("http://www.nvnews.net/vbulletin/showthread.php?t=104713") bug...

---

### Post by Elle Stone on 2007-12-31
Hmm, that is an interesting bug over in the nv forums.  But I don't think it's the same problem.  My fan only runs on high when I start wine.  For any reason, even just winecfg.  I don't run any 3-d applications, and indeed a check of the gpu temp shows it at normal levels.  The problem is specifically and only when starting wine.  After some length of time, maybe ten minutes or so, the fan slows back down again, whether or not wine is still running.  Starting and shutting wine down immediately doesn't stop the fan from spinning rapidly - it still takes a few minutes to stop even if wine was only up for a minute.  But the only time the fan spins up is when I start wine.  The rest of the time it is very quiet.  So I think it is wine-related, or wine-nvidia related. 

My nvidia drivers came from the restricted repository rather than straight from nvidia, if that makes a difference.

Elle

---

