---
title: "Output volume on Ubuntu 12.04 : how to set it so it remembers?"
date: 2013-11-14
forum: General Help
---

### Post by Richard_York on 2013-11-14
We're fairly new to Ubuntu and mostly loving it.  Windows - good riddance!

I know how to bring up the output volume to the speakers: click on the top-right "System Settings", then on "Sound", and slide the output volume up from its default midway position. This makes our weak little laptop reasonably audible.
But then each time, it forgets, and returns to default.

Is there a way, please, of telling it to stay at the new setting so it remembers between sessions?

Thanks

---

### Post by stinkeye on 2013-11-14
Test this command in the terminal to see if it changes your volume when set to half, to full.
```
pactl set-sink-volume 0 100%
```
If it works add to startup applications.

---

### Post by Richard_York on 2013-11-14
Thanks for this.  It works... but.... 
The laptop machine is so puny it needs 120% of volume to be audible, so I amended your instruction to read 0 120% instead of 0 100%.
I'd never tried to alter the startup Applications before. It worked, and on a restart, the volume is where I want it, but on the one re-start I tried, something evidently was unhappy, as after a pause several "crash report" lines appeared, then a much longer pause ( not as long as Windows starting, but enough to make me wonder if somehow I'd done something distastrous!) before it came to life properly.
Would you expect this to happen?

... So for an experiment, I just tried removing it again from Startup App's and restarted, when it all opened up faster again, though still a little slower than originally, I think. Interesting.

---

### Post by stinkeye on 2013-11-14
> **Richard_York said:**
> Thanks for this.  It works... but.... 
The laptop machine is so puny it needs 120% of volume to be audible, so I amended your instruction to read 0 120% instead of 0 100%.
I'd never tried to alter the startup Applications before. It worked, and on a restart, the volume is where I want it, but on the one re-start I tried, something evidently was unhappy, as after a pause several "crash report" lines appeared, then a much longer pause ( not as long as Windows starting, but enough to make me wonder if somehow I'd done something distastrous!) before it came to life properly.
Would you expect this to happen?
Not really.Probably not related to the added pactl command.
Maybe give the command a slight delay.
In which case use this as the command in startup applications...
```
sh -c "sleep 10 && pactl set-sink-volume 0 120[COLOR="#FF0000"]\[/COLOR]%"
```

[COLOR="#FF0000"]Edit [/COLOR]I had to escape the % with a backslash for the command to work in startups.

PS You can go up to 160% and you can test with a log out/in.

---

### Post by Richard_York on 2013-11-14
I'll try that, thanks. Just now have to switch off & do other stuff, so will try tomorrow.
Thanks for your help!

---

### Post by Richard_York on 2013-11-16
With apologies for a slow reply - just got chance to try this, and with even more thanks, it works and seems fine! I didn't know about testing with logout/in either, so that's good too. I haven't yet tried a shut-down/restart but the log-in test worked perfectly.
I don't pretend to know how the syntax of the command you quote works, but as it does, I'm happy!
Best wishes

---

### Post by stinkeye on 2013-11-16
> **Richard_York said:**
> With apologies for a slow reply - just got chance to try this, and with even more thanks, it works and seems fine! I didn't know about testing with logout/in either, so that's good too. I haven't yet tried a shut-down/restart but the log-in test worked perfectly.
I don't pretend to know how the syntax of the command you quote works, but as it does, I'm happy!
Best wishes
Glad it worked.
You can glean a lot from the manual pages...eg in terminal
```
man pactl
```

---

### Post by Richard_York on 2013-11-16
Again thanks... likewise for the manual pages, which of course I hadn't spotted!

---

