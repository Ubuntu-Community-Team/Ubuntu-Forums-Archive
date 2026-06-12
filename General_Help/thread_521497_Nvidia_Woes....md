---
title: "Nvidia Woes..."
date: 2007-08-09
forum: General Help
---

### Post by dartmusic on 2007-08-09
I know that this has been addressed multiple times, but because of the nature of the problem there have been many different solutions offered, though no real definitive answer has been noted/listed/posted/etc.

I'm running a 3.2Ghz P4 with 1GB of RAM, a GeForce 6200 and a Hauppauge PVR 150.  This machine is mostly used to run MythTV in my living room.  When I was running Dapper and a 5200, I had no problems installing the nvidia driver via Automatix.  When I upgraded the video card (mostly to get a card without a fan), I had trouble getting it to run.  I upgraded to Edgy, and none of the "easy" solutions would work to get the nvidia driver to load and run properly.  I tried downloading from the nvidia site and following their instructions, which worked perfectly.

Last weekend something in my system failed and I couldn't get the dvd drive to eject a cd after I had burned it.  I had to take apart the box to get at the release to get it open and out.  When I put it all back together, the video driver wouldn't load and I got a black screen and a broken X server.  I don't know how these are related, but nothing is physically amiss (in terms of my opening the box and putting things back together), as when I change the driver in xorg.conf to "nv" everything works fine, except, of course, MythTV.

I upgraded to Feisty to see if that might help (with the new restricted drivers manager), but no love.  I've tried every method: Automatix, Envy, apt-get install nvidia-glx (and glx-new), manually installing the drivers from the nvidia site, but every time I get some sort of crazy X error.  At first it was the API mismatch error and now I get the "cannot load nvidia module" or something along those lines.  And now when I try to install manually, the build process fails, where it didn't previously, and no explanation as to why.

Has anyone come up with a sure-fire fool-proof way of a) clearing out the detritus from attempting to install these drivers repeatedly and b) getting any of the three latest driver versions to actually work?  I know that some people have, but not everyone has had success. 

Any help/helpful hints/etc., would be GREATLY appreciated.  

Thanks!

---

