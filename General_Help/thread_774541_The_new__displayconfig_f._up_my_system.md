---
title: "The new  displayconfig f. up my system"
date: 2008-04-29
forum: General Help
---

### Post by olavjunior on 2008-04-29
So there it is again, the time that I have to fight with xorg and gnome display. 

If you don't want to know the story behind, you can skip this:
The story short is that I was to connect a projector at school. I have a easy script that I use when I connect my tv or projector at home, just copying a xorg.conf.tv (ex) to xorg.conf and xorg.conf.regular to xorg.conf when I'm done. 
The thing is that the resolution was wrong compared to my projector at home, so I'd read somewhere here on the forum a guy who was so happy with the new gnome displayconfig, that it easily changed the resolution and stuff. So I tried it out. (Should never have....)

I got two screens on my screen, with a split in the middle. And using my good old working xorg.conf just doesn't do it any more! Something (gnome displayconfig) is overriding it! I managed with the projector connected to get the right resolution through displayconfig, but after reboot, everything is messed up again, and now I have a resolution like 800x600 instead of 1280x800. If I use my old xorg.conf now, it will result in a split screen, with mouse appearing a complete different place than it really is. 

I'm really messed up. Didn't think this would ever happen again, I've gotten so much training in the xorg.conf...damn!

So, how do I show the finger to gnome displayconfig and use xorg.conf and nothing but??

You can see from my picture how the desktop looks after going back to org xorg.conf.(You see that a regular screendump won't do, it seems quite normal) Then with altering with displayconfig I can get right resolution after a while (when I'm lucky) but it won't stay that way after reboot. Then me res is 800x600.

---

