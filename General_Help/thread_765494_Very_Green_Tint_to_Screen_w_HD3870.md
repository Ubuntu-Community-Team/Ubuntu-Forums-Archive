---
title: "Very Green Tint to Screen w/ HD3870"
date: 2008-04-24
forum: General Help
---

### Post by absoluthamm on 2008-04-24
I am not sure about this, but I just installed Hardy to my recently built computer and when I start up the computer with it it will go through the loading screen fine, but then after it loads completely and then goes to show the desktop screen, everything turns to a very obvious tint of green. I have looked at my monitor settings and everything is fine there and everything is still perfect in Windows, but for some reason it is this tint of green over the whole screen. I am thinking that it is the video card, which is an ATI Radeon HD3870, but I am not sure what else it would be. I tried searching google and the forums for people with this similar green problem, but I couldn't seem to find anything. Any help would be much appreciated.

AbsolutHamm

---

### Post by retrow on 2008-04-24
Check the VGA or DVI cable that runs from your video card to your monitor's data port. See to it that its plugged in and screwed in properly. Oftentimes when there is an open connection on the red/blue data lines, the picture ends up looking all green. Conversely, it can also end up looking red or blue if other lines are open.

---

### Post by absoluthamm on 2008-04-24
As far as I can tell this is not the issue. Especially since everything is fine in Windows XP and also everything is fine with the loading screen of Ubuntu, just when it loads the desktop it goes green tinted.

---

### Post by acowboydave on 2008-04-24
> **absoluthamm said:**
> As far as I can tell this is not the issue. Especially since everything is fine in Windows XP and also everything is fine with the loading screen of Ubuntu, just when it loads the desktop it goes green tinted.

I had a similar problem, not running any Win. on the Quad..turned out to me a loose connection..might double check it..wont hurt..:-)

---

### Post by djrobthaman on 2008-04-25
I'm having the same exact problem.  And to go a bit further, if I install the ati driver for my video card I then get no video output.  If you figure this one out, let me know how you get it working.

---

### Post by absoluthamm on 2008-04-25
I tried replugging the cable in to both the monitor and the video card with no change. Any other suggestions?

---

### Post by guerilla on 2008-04-27
i have the exact same problem. i was using gibbon fine but then when i installed heron the screen had a v ery green tint to it. i know the cables are fine because i am using xp on the same computer and its fine. also whe ubuntu loads up the ubuntu logo is the correct colours. Im using an ati x1300

---

### Post by djrobthaman on 2008-04-27
I don't know if this will help anyone, but I fixed my problem, which was very similar.

[You can see what I did here.]("http://ubuntuforums.org/showthread.php?p=4815326")

---

### Post by absoluthamm on 2008-04-29
OK sweet. So let me get this straight in a step by step...

1. Reinstall with Gutsy
2. Copy the xorg.conf file somewhere
3. Reinstall Hardy on the computer
4. Update ATI Driver
5. Replace copied xorg.conf file

I wasn't sure which came first, 4 or 5. Thanks for the response.

---

