---
title: "monitor resolution dropped from 1920x1080  to 640x480; can't restore"
date: 2014-03-24
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-03-24
tldr summary:

Screen went black and hung. Rebooted and the monitor resolution had dropped from 1920x1080  to 640x480.  Tried to reset resolution with xrandr and  it reported that 640x480 was the only available mode. The nvidia-settings gui is extremely difficult to use with the rez like that but I did manage and it says something like it can't connecct to x. Which seems nuts because how could I see nvidia-settings itself if x isn't working?

It's not a hardware issue because I have a nearly identlical system on another partition of the same drive and it works normally.  I purged nvidia*, thinking the non-propietary driver might work. It didn't. I reinstalled nvidia-current. Didn't help. I purged it again and installed a higher number, nvidia-319 I believe. No change. I looked at both xorg.conf files and they were a little different so I copied the one from the working system over the one in the broken system.  No change.  For my next step I was thinking of purging and reinistalling xorg. That will take a long list of gui aps with it but I can reinstall them too.

The system is 13.10, 32 bit, Openbox (like in Lubuntu)

Anybody got a better idea?

---------------------
That's a pretty good summary but I posted 
some more details in a perhaps too long post here:
[http://ubuntuforums.org/showthread.php?t=2212531](http://ubuntuforums.org/showthread.php?t=2212531)

---

### Post by Dreamer Fithp Apprentice on 2014-03-24
tldr summary:

Purging xorg* and reinistalling xorg worked.

More detail in my original thread for anyone interested.
[http://ubuntuforums.org/showthread.php?t=2212531](http://ubuntuforums.org/showthread.php?t=2212531)

---

