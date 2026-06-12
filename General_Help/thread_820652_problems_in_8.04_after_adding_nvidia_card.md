---
title: "problems in 8.04 after adding nvidia card"
date: 2008-06-06
forum: General Help
---

### Post by rudy.elgato on 2008-06-06
So a few weeks ago my old MS2000 home desktop system went completely belly up.  Details of it's problems don't really matter other then to say it convinced be to go ahead and move to Ubuntu 8.04.  So, downloaded the iso image, burned to cd on my office system.  Took home, and that initial installation on my home desktop went great.  Everything installed just fine and started up just fine.  I downloaded and installed additional packages and those also ran smooth as silk.   Poked around some more about the 3D eye-candy available via Compiz and thought why not.  So I found an older Nvidia GeForce FX5200 128MB, installed it, updated what needed to be updated on the system/os to get the fancy stuff running, which worked fine.  

But....  Other things which had been working fine on the system prior to the video card suddenly stopped working fine.  Specifically:

1. Switch User stopped working.  Before adding the video card I was able to bounce between me, my wife's, and my daughter's userids without any problem at all.  Now, I can bounce once, maybe twice, then the monitor just turns white and doesn't respond.  I have to run a ctrl-alt-backspace to kill the gnome window manager, and then log on again.  This is kind of an issue because I would really like to let them have their own userids, their own profiles on the system and make it as seamless as possible to bonce between userids. 

2. Suspend stopped working.  Before, when I was finished using the computer and I knew I wasn't coming back to it for awhile I could select Suspend and the system would quietly go into suspend mode.  I could then push the suspend/start button on the desktop  and the system would quickly come back to life at the password screen.  Enter my password and I'm right back on the system.  Now, the system doesn't come back from suspend.  The monitor doesn't seem to respond and the only way to get things back is to physically power off/on the system.  This is kind of an issue because I would really prefer not to have the system running when it's not being used and would like to have it available as quickly as possible when someone does need to use it.

3. Fullscreen flash video does not run smoothly.  Say, if I go to hulu.com, a video run in the small default screen runs great, but runs herky-jerky when I select fullscreen.  Prior to adding the video card, a fullscreen view from hulu ran smoothly, just not real clear.  This was actually one of the reasons I wanted a better video card.  I thought it would present a clearer picture.  Well, the fullscreen picture is clearer, it just runs terribly choppy.

Been searching through the forum here, and other places, and believe these issues have been run into and reported by others.  I just haven't been able to come across anyway of correcting them yet.

Any ideas, help, suggestions, are truly appreciated.

Thanks...

---

### Post by Titan8990 on 2008-06-06
Are you sure that you have the latest drivers for your card installed?

If you are not sure:

#apt-get install envy

Envy will uninstall your old drivers, search for new ones and install them (maybe not in that order but you get the idea).

---

### Post by rudy.elgato on 2008-06-06
I've read about 'envy' but have not yet tried it.  I presumed that enabling the nvidia driver via "Hardware Drivers" would have installed the latest driver for the card.

I'll definitely give 'envy' a try as soon as I'm in front of my home system.

Thanks for the tip...

---

