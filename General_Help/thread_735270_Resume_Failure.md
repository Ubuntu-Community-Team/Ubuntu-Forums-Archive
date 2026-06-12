---
title: "Resume Failure"
date: 2008-03-25
forum: General Help
---

### Post by jcobban on 2008-03-25
I have not been able to get Suspend/Resume to work.

I have just moved to Ubuntu 7.10 (Gutsy Kernel Linux 2.6.22-14-generic) from Windo$e, so perhaps I am just not aware of exactly how to set this up to work.  I am running on a 2.66MHz Intel Celeron processor using the internal graphics support.  When I resume from suspend one of two things happens:

1) On resume the display shows a garbage bit pattern. :( The system is apparently functional, but I cannot determine exactly which sequence of keystrokes to enter because I cannot see the dialogs that are displayed to me.  If I click on the upper right corner, where the "power button" icon should be, the bit pattern on the screen shifts in a rectangle corresponding to the dimensions of the shutdown dialog, but there is no dialog visible.  I can tab between the options on this invisible dialog and, for example, log out of the session.  At this point the screen is refreshed with the login and I can proceed from there.

2) On resume the screen is black except for the arrow cursor. :( If I Ctl-alt-F2 at this point I see the following messages:

kinit: trying to resume from /dev/disk/by-uuid/b3........
kinit: no resume image, doing normal boot
login:

So I login and issue "sudo reboot" to get the system back.

Although I am aware of the threads regarding problems with suspend/resume, I do not see any that match my symptoms.

My Linux knowledge is weak.  Many years ago I used Solaris for a few years and the knowledge is coming back slowly.  So please be patient with me.

---

### Post by mlapaglia on 2008-03-25
i think the suspend option for ubuntu is crippled by the lack of video driver support. I know for ATI cards they can't suspend or hibernate because the video card doesn't support it.

---

### Post by vprasaj on 2008-03-29
> **mlapaglia said:**
> i think the suspend option for ubuntu is crippled by the lack of video driver support. I know for ATI cards they can't suspend or hibernate because the video card doesn't support it.

That's strange. I have two machine and ati is working out of the box. I have most problems with my nvidia card.

(ATI 9800SE, NV6600gt)

---

### Post by HuckleSmothered on 2008-03-29
I had some similar, but not exactly the same, problems with my resume. 
Playing with the video drivers did help.
I ended up installing ENVY.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
This is specifically for installing the exact NVidia driver your system needs.
Quite nice.

---

### Post by jcobban on 2008-03-31
I am not running a video card, whether NVidia or otherwise, just the on-board graphics.  Furthermore one of my problems does not appear to have anything to do with the video card, since the error message explicitly refers to a missing resume image.

It is important to me to be able to save energy.  That is one of the decision points that led me to choose Ubuntu.  But neither Suspend nor Hibernate work on my system.  I do not like having to completely shut down my system and then have to boot it up again later just in order to save power.

I would really appreciate some direction from the community about where I should look to resolve this problem.

---

