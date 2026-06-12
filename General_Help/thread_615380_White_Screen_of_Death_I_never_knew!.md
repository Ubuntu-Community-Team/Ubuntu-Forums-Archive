---
title: "White Screen of Death? I never knew!"
date: 2007-11-17
forum: General Help
---

### Post by Red.Heron on 2007-11-17
Okay, I've read the other "white screen of death" reports, and mine appears to be related in one way, but the effect manifests slightly differently. I'm using the nVidia drivers (as that's who made the entire chipset for my mobo), and I've noticed that the windows that turn black generally have permissions issues from sloppy install scripting. Once I re-change the directories of a program back to what they should, the problems magically disappear with that.

However, I've got a very strange "white screen" issue that seems to appear only when my wife's account is active at the same time as my own. Being the good Windows user she was, she uses the "switch user" option, and then logs out of her account when she's through... at which point the screen has invariably gone white with the standard white cursor. Being the ultra-patient sort (which you have to be to use Windows for as long as I have), I saw the white screen and stepped away, cooked dinner, ate, fed the kids, and came back... and it was still white 45 minutes later. Since I didn't have a clue as to how I should fix anything, I tried the CTRL-Fx keys, the ALT-arrows, etc., and nothing seemed to respond other than the mouse. I didn't even detect any disk usage (no flashy-flashy on the little HDD light). I wound up having to do a hard reboot. This is about the fifth or sixth time it's done this, and I'm not sure what to do about it.

Any help would be greatly appreciated. I would especially appreciate it if nVidia released their hardware specs enough that programmers could actually program an open driver for it. So long as we're not duplicating the hardware, no patent infringement right? And that's also why God gave us reverse engineering, right? (Just kidding about that... wouldn't wanna get anyone in trouble, but do you know what I mean?)

Thanks, and I hope someone's got some insight into this... I can't crank up my screen res without those !@#$# drivers, and I need the real estate for the type of work I do (financial data correlation).

Sincerely,

Red

---

### Post by HermanAB on 2007-11-17
Hmm, well, Ctrl-Alt-Backspace will restart X.  That is probably the only thing you can do.

---

### Post by Red.Heron on 2007-11-17
Tried that, but I can't log back in to any account once it happens.

And in addition, I can't change the screen resolution... it tells me it succeeded, but the resolution isn't actually different. This suggests to me that I should test the video driver.

How do I uninstall my non-free nVidia driver?

---

### Post by hotani on 2007-11-19
I can consistently reproduce this by switching to another user, then attempting to switch back to my own account. This produces the WSOD. I'm using gutsy with nVidia as well, but am not having the other problems associated with nVidia 7xxx cards such as black windows and/or black flashes or system hangs.

Only way out of it is ctrl+alt+backspace.

---

### Post by VSpike on 2007-11-20
I have the same issue when switching users on a clean install of Gutsy (wsod).  No other effects related problems that I've seen, but since I also have a wife, the user switching is a must-have and therefore the eye-candy goes!

Before this, I was running Feisty using the latest builds of compiz-fusion and the bleeding-edge nvidia driver (installed with Envy).  I had exactly the same problem there too, which is odd because according to at least one person in #compiz-fusion (and also the driver release notes) this is a known bug that should be fixed already!

Back then, I was using the compiz icon, and used that to enable "indirect rendering".  I know this can be done from the command line too but I've never done it.  This does cure the problem.  Unfortunately this also loses the main benefit of the compositing (for me) which is a flicker-free window manager.  And it caused some lousy performance on video playback.

I'd really like to see a solution for this bug!

---

### Post by JonGoldberg on 2007-11-21
Hey everyone,

I have the same problem, did some Googling, found this bug on Launchpad, and found a VERY useful tip:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/78470/comments/27](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/78470/comments/27)

In short, when you get the white screen, press Alt+S, and you get a new login prompt, and you do NOT lose your work!  I just tested it now and it worked for me, though YMMV of course.

---

### Post by VSpike on 2007-11-21
Good tip, thanks!  Still think I'll leave the effects turned off though.  

It sounds like metacity will get some compositing support of it's own soon (just to eliminate flicker and allow proper transparent windows and drop shadows) which I think would be a better solution for me.  

But I guess this bug is at the driver level or kernel level, so we'll have to wait for nVidia to fix it.

By the way, I just remembered -- my problem in feisty was a black screen with a mouse cursor but no response to any keypress.  If you Google, both the white and black screens are common problems.

---

