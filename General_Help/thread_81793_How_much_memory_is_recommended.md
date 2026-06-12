---
title: "How much memory is recommended?"
date: 2005-10-25
forum: General Help
---

### Post by mev on 2005-10-25
How much memory is recommended to run Ubuntu?

I have a laptop with 256Mb of memory.  I tried an experiment to run a virtual machine under VMware vmplayer, and in that virtual machine, I have another instance of Ubuntu running as well.  So the memory situation:

Virtual machine: 96Mb
Host machine: 256Mb - 96Mb = 144Mb

This combination seems to take forever to run.  I can play with adjusting this but am curious if I should expect the situation to get a lot better if I update the laptop to have 512Mb of memory...

--mev, Mike Vermeulen

---

### Post by drummer on 2005-10-25
You can also try running the live cd, then you'd be using the full 256meg of ram. 256 should be enough to run either Gnome or KDE theoretically. I haven't used ubuntu on a machine with that ram so can't compare performance to one with 512 (mine) but it would of course be faster when running more programs.. like firefox, open office, gimp, etc... 

Both Gnome and KDE use about 130megs of ram on their own, with no other programs open, so the situation you had probably had just 14 megs left for everything else which is definately not enough to run FF, etc without using swap too.

Try the live cd or install ubuntu and if it's not fast enough for you, up the ram.

---

### Post by Staesys on 2005-10-25
In my experience...

The LiveCD takes forever to do anything and is slow. Sorry, that's just a fact. It's that way on every computer I've tried it on. I can start Open Office and go eat supper, and when I get back it's just opening the main window.

That said, it does work just fine.

At this very moment, I'm running BB on a computer with a total of 256MB RAM (2GHz proc) and it runs just fine. I've also got a decent video card. How fast/good your video card is, is going to be a major factor on how fast your computer runs, in my experience. I'm going to upgrade my memory to 512MB ASAP, but only because it'll speed the system up a bit more. It's perfectly usable the way it is.

I hope this helps!

---

### Post by mev on 2005-10-25
[QUOTE=drummer]
Both Gnome and KDE use about 130megs of ram on their own, with no other programs open, so the situation you had probably had just 14 megs left for everything else which is definately not enough to run FF, etc without using swap too.
[/QUOTE]

Thanks, seems like more memory is useful here if I'm going to run two copies on Ubuntu on the same laptop (one is the host machine, a second is the virtual machine).  Most likely, my virtual machine @ 96mb is going a lot to virtual swap...and the host machine is KDE + virtual machine + normal system processes...

I'm not quite certain how a live CD should alter the amount of memory being used, since doesn't it mostly replace what comes from the filesystem?

--mev, Mike Vermeulen

---

### Post by tonysathre on 2005-10-25
i dont see how a live cd would help either cause i thought that live cd's were placed and ran completely from memory

---

### Post by Thorsten on 2005-10-25
[quote=mev]How much memory is recommended to run Ubuntu?

I have a laptop with 256Mb of memory.  I tried an experiment to run a virtual machine under VMware vmplayer [...]

[i] am curious if I should expect the situation to get a lot better if I update the laptop to have 512Mb of memory...
[/quote] 
As others have pointed out, running Linux inside an emulator or from a live CD doesn't give a good prediction of the performance of a Linux hard disk installation.

I can only tell you that I have Debian Sid w/KDE (which is very close to Kubuntu) with all the bells and whistles (incl. two simultaneous X sessions) running quite comfortably on a PC with 384 MB of RAM. 

If you don't need all the bells and whistles (e.g., transparent menus and panels, elaborate dynamic backgrounds, anti-aliasing with lots of fonts), you might be OK with 256 MB of RAM for most situations. If that turns out to be a little too sluggish, 512 MB should be sufficient.

HTH,
Thorsten

---

