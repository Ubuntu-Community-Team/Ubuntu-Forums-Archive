---
title: "[SOLVED] gtkguitune not recognising input"
date: 2008-03-27
forum: General Help
---

### Post by bryncoles on 2008-03-27
hi everybody!

just noticed something very annoying today. i booted up gtkguitune, to tune my guitar (im only learning - i cant do it by ear yet), but found that gtkguitune wouldn't or couldn't pickup any sound. not from a microphone plugged into the line in (thats how i usually use it), nor from a mic plugged into the mich jack, nor from my laptops internal mic. 

this annoyed me, because it was working fine last time i tried it (which was about a month ago ill admit). 

i have no idea how to check the settings or diagnose the problem, ive only been in 'buntu since january. 

anybody got any ideas as to what i can try? if ive not posted enough info, just let me know what you need and how i can find it out!

oh - im using a packard bell easynote r4360. 

thanks in advance!

oh - if i start it from terminal i get a load of messages along the lines of 'Gdk-CRITICAL **: file gdkdraw.c: line 212 (gdk_draw_string): assertion `drawable != NULL' failed.', if that helps anyone...

---

### Post by bryncoles on 2008-03-28
problem solved! yay! i found the problem was actually more severe than i thought, when i tried to do some recording in audacity. i had no sound input at all. 

turns out that theres an extra option in alsa mixer called capture. somehow, somewhere down the line this had been muted. probably when i was p*ssing about with my settings! re-enabling that has solved my problem, and i have sound input back! yay!

also: red-faced!

---

