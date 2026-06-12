---
title: "Running tasks are stopped when activating screen lock"
date: 2017-12-19
forum: General Help
---

### Post by ronquises on 2017-12-19
**System and settings:**
&#8226; I am using Xubuntu 16.04 LTS
&#8226; In "energy settings" I disabled all "suspend" and "stand-by" options (set them to "never")
&#8226; I enabled screen saver after 15 minutes.
&#8226; I enabled screen lock 1 minute after screen saver activates.

**Problem:**
**Whenever screen lock is activated (be it automatically or when I do it manually), then ALL running tasks are stopped.**

**Description:**
I am running an ownCloud-Client on my PC, which stops to synchronize whenever screen lock is activated. Only after I disable screen lock by entering the password, the synchronization continues.

I also tested this with playing music from youtube in a browser, locking the screen stopped the audio playback.

I tested it on a different PC using Linux Mint Cinnamon, where the audio playback continued. Only the screen was locked, as it should be.

Now while I don't particularly care about youtube playback, I very much care about the ownCloud synchronization, which **OBVIOUSLY should continue despite the screen being locked.**

**Expected behaviour:**
Tasks should continue to run, when screen is locked (I am aware that "screen" is a window manager).
Basically I would like **to automatically lock just the desktop**, not the whole screen/session.

**Question:**
Is there a persistent way (i. e. not something I have to do manually every time I start the PC and/or the ownCloud-Client) in Xubuntu to achieve the above mentioned?

**Note:**
I am not looking for a solution, which turns off the "screen lock" globally, I very much want the screen to be locked when I am afk.

Thanks for any help and hints!

---

