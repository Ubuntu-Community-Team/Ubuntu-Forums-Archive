---
title: "Slow Gnome boot time with IPW2200"
date: 2005-08-16
forum: General Help
---

### Post by IronKnuckles on 2005-08-16
I'm not sure what forum this should be in, so if this is irrelevant here, please move it to the correct place.


I have been dealing with an issue related the IPW2200 and Gnome. Specifically if takes waaay too long to go into standby (suspend to RAM) to be useful on a laptop. The same slowness occurs when starting up Gnome for the first time. I determined that the slowness was caused by IPW2200; when it is disabled, Gnome boots with a normal speed and standby is similarly normal.
(Note: The IPW2200 connection is eth1)
My current method for solving this problem is ridiculously inconvenient, but I have a feeling it could easily be automated by some shell scripts. I however do not know enough shell to write such a script.
What I do is:
1. In Gnome menu: Applications > System Tools > Network Tools
    Select eth1... Configure... Deselect "This device is configured"
2. Go into standby (I just close the lid on laptop)

This eliminates the 5 minute wait I used to have to endure before my laptop would *actually* go into standby. How can I automate these steps?

Also, in order to eliminate the wait when I boot (ie: not from standby), how do I change the settings in Gnome so that IPW2200 does not connect by default before Gnome has loaded?

Thank you

---

