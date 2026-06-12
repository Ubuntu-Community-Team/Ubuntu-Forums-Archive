---
title: "Won't Boot After Installing runit-run"
date: 2007-09-04
forum: General Help
---

### Post by somedamfool on 2007-09-04
I've used Fedora since core 1, and decided to try Ubuntu, so a few days ago I installed it on a separate hdd and installed KDE. Everything worked fine until today. Synaptic had warned me on a few occasions it couldn't continue an install because runit wasn't configured. I did a search and my understanding was that runit needs runit-run, so I installed it.

Now Kubuntu won't boot. The boot process starts, then the computer shuts off. The last thing I see on the screen is: poweroff /dev/hda. I tried the rescue kernel but it says there isn't one. I booted the Ubuntu DVD and I can see and browse my OS on /dve/hda. That being the case, is there a way I can fix this; restore some files, change lines in a config file, or something?
Thanks,
Mike

---

### Post by ethebubbeth on 2008-02-27
I am in the same boat here on gutsy... 

I used sudo aptitude install runit-run, which also instaled runit.

My system now boots rather quickily... and then immediately quickly without any option for user input.

---

