---
title: "feisty broke beryl, Xorg too?"
date: 2007-04-26
forum: General Help
---

### Post by ac251404 on 2007-04-26
I just upgraded to Feisty on my Thinkpad X31. Previously I was running Edgy with Gnome/Beryl and everything was working okay.

After the upgrade everything looked fine and I attempted to login. After seeing the splash screen and my desktop for a moment, it crashed back out to the login screen. Tried the failsafe gnome session with no luck. Then I went to the terminal and was going to try disabling the beryl-manager in session start-up, but I couldnt figure it out so I just used apt to remove the beryl/beryl-manager packages. So now I can log in and everything looks good except dragging windows is very choppy/sluggish. I decided to check out my cpu/mem stats (using top) and noticed when I was moving a window Xorg would jump as high 90% cpu usage. I have never seen Xorg use near that in the past, so I now I am sure something is wrong with my video drivers or Xorg, but I am not sure where to start diagnosing the problem. Everything else appears to be fine, even scrolling in Firefox and other apps (which was a problem I originally had with Edgy). 

So does anyone have any idea what might be causing this or know where I can start looking for more info? Google hasn't been very helpful, I guess because Feisty is so new?

Thanks,
-Alex

---

### Post by palmerthegeek on 2007-04-27
ac251404
What is your video card?

---

### Post by ac251404 on 2007-04-28
its a radeon M6LY I believe. 16MB onboard chip.

---

### Post by all2ez on 2007-05-05
I got beryl in feisty working on my laptop.  I have a thinkpad T60 with ATI Radeon Mobility X1400.  I have a triple boot system with XP, Vista and Feisty...  I had Edgy and beryl working, then I upgraded to Feisty and beryl was still starting when I logged in, but it wasn't working.

I looked around a few places and found no help, so I just uninstalled all of the beryl stuff through synaptic in System>Administration>Synaptic Package Manager (just search beryl and mark everything that is installed for complete removal).

After that, I basically followed the guide here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

and it works!!!

It seems the key was editing the startxgl.sh that I already had.  Also I had to disable the universe repository and add the correct repository to install beryl from (deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main).  Oh and the ATI restricted driver has to be checked enabled.

Hope this helps, this is my first forum post!

:guitar:

---

