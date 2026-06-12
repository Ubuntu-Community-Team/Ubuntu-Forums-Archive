---
title: "Ubuntu 8.04 CPU 100% Xorg the Problem?"
date: 2008-06-12
forum: General Help
---

### Post by Relysis on 2008-06-12
I am using a Dell Inspiron 6000 laptop with Hardy Heron.  It has an Intel Pentium M 2.13GHz, 2 gig ram, and ATI Radeon X300 video card.

When I use any slightly cpu intensive application, the cpu skyrockets.  I have tested this using the open video driver as well as the ATI proprietary driver, and the results are the same.  Disabling desktop effects also have no effect.  

It always goes to 100% when watching a video in firefox, but I have read in other threads that this is a common problem with linux flash.  However, doing nothing more than scrolling in Firefox can make Xorg spike to more than 50% usage.  Many other application such as MPlayer, K3B, ManDVD, Gens, Wormux, etc, also shoot the cpu to 100%.  I cannot watch a video or burn a cd without the computer shutting itself off due to overheating.  

That said, I have noticed that top almost always shows the Command Xorg as the problem.  It is run under root, and is always taking up the most cpu.  It shoots up when I run applications.  For example, opening wormux makes Xorg shoot up to 80% cpu (according to top).  This is reproduceable with many other applications.  Watching a fullscreen Vcd in MPlayer, Totem, or VLC causes Xorg to shoot to 80% (the player being 17ish).  As you can see from the laptop stats, this shouldn't be happening, as it has no problem running all these applications at once in XP.

I would love to know if Xorg is really the problem, and if I can fix it.  I don't want to dump Ubuntu, but more importantly I don't want to fry my cpu.  I have read other threads with similar problems, but could not find any real conclusion.  Any help would be greatly appreciated.  I will check here frequently.  Let me know if I need to post any output.  Thanks a lot!

---

### Post by AndThenWhat on 2008-06-12
For a temporary fix, you could try changing the process's priority to something lower. 
(Go To System -> Administration -> System Monitor)
That way it won't freeze your computer trying to run a Firefox video.

---

### Post by Relysis on 2008-06-14
This didn't seem to fix the problem, even with the browser.  I believe it is strictly a Xorg problem.  Thank you for your input, I still didn't know this was possible to do from the system monitor.

---

### Post by TheBluntNinja on 2009-06-02
bump

---

