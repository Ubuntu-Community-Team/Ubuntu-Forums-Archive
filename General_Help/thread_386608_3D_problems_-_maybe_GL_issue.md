---
title: "3D problems - maybe GL issue"
date: 2007-03-17
forum: General Help
---

### Post by Cannonade on 2007-03-17
I have a GeForce 7600GT. Now, I now GL works fine in Windows and there is no problem with the graphics, everything, games, programs, screensavers, etc run perfectly smoothly.

The 3D screensavers in ubuntu, like my favourite the flying toasters all run a little choppy. I downloaded Celestia, which I run in Windows, to see what it was like in Linux. God, it ran as slow as anything! I had no idea why. I checked in synaptic, I had the nvidia drivers installed.

I downloaded this program Automatix to get the non-free codecs for DVDs, etc. I noticed that it had nvidia drivers in, so I downloaded them, perhaps stupidly. The next thing after reboot, none of the 3D applications run. Celestia closes down and none of the 3D screensavers appear, they just show a blank screen in the preview. I tried removing the drivers installed by Automatix, still the same problem.

Other than these mysterious drivers, the only other thing I've done is edit the xorg.conf file so 1280x1024 no longer appears because my Monitor doesn't support it. Any ideas on what is causing this problem? I do miss the flying toasters!:cry:

---

### Post by jolan_jj on 2007-03-17
I have the same issue with the screensavers with nVidia 6800XT. 3D graphics and direct rendering is enabled and ok, I run Beryl window manager on dual screen and it runs smoothly. But the graphics generally (like opening window, scrolling i Firefox and things like that, and choppy screensavers - both 3D and 2D) is a bit "delayed". When I use Metacity instead of Beryl though, the screensavers run fine. It can be a Beryl/AIGLX and OpenGL issue. Anyone has the same problem, or maybe someone has a solution?

---

### Post by Cannonade on 2007-03-24
Originally, the problem was similar to the same kind of thing I get on my laptop. Really choppy 3D graphics, as if my graphics card cannot handle it. I know on my laptop, that IS the problem, because of an S3 Savage Twister card...:oops: 

I thought it maybe a driver problem, because I know from running Celestia that this is no the problem. 2D applications run fine, like the games and some of the 2D screensavers. So I found those drivers listed in Automatix and downloaded. Ever since then, anything that uses 3D no longer works. Celestia no longer opens and the 3D screensavers stop showing.

I've tried looking here and tried doing some googling, but no success. I can't really think of anything short of reinstalling ubuntu and seeing if that fixes things. But I'm quite lazy, and don't really fancy doing that.

Thanks in advance for any help.

---

### Post by jolan_jj on 2007-04-21
The funny thing is that now i'm using the onboard graphics (it's an Intel i945, I think) with beryl on AIGLX, and the video is working just fine! The 3D performance is of course much decreased in comparison with nVidia card (6800XT) which I normally use - now i'm making a waterblock for it so I had to remove it from the computer. But video works smooth and screensavers work properly and use much less ressources than with nVidia. And the weird delay when I f.ex. open a new tab in Firefox is now also gone... I have a suspicion that it's some kind of nVidia drivers issue. Doesn't anyone else have it and/or solved it? I'd like to get rid of the problem when I finish my watercooling system...

---

