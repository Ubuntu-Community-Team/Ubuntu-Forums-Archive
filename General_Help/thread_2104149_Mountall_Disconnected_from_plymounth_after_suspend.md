---
title: "Mountall: Disconnected from plymounth after suspend"
date: 2013-01-12
forum: General Help
---

### Post by tudstudent on 2013-01-12
Hi, this is my fipo here.
I am not a experienced Ubuntu user, but trying my best to give as much information as possible.

I used to use Opensuse for over 10 years and recently I found out it was not smoothly working with bitstream and XBMC. Time to switch...


So for my HTPC I have installed Ubuntu mini and installed afterwards necessary packages for XBMC from GIT but also for Nvidia-current (313 package).
I have upgraded my kernel by using the kernel.org package and made an .deb file.
Kernel is working fine, but the reason I upgraded the kernel was coz I hoped it solved my issues with plymouth.

Each time if I put the system for a long time in suspend after a wake-up call the message appears in console:

```

mountall: disconnected from plymouth

```

However when I restart XBMC with my init script it works again. (I do nothing with this error and I do the restart by SSH)

Strange thing is that I do not have any problems during boot. After this message I need to pres the off button. Systems shuts down. I restart the system and it boots to command line. Then I again press the off button and after that I restart the system again.... And then it loads XBMC again. Prob a safety feature of Ubuntu.

Though I cannot find the log where this Mountall error is logged so I can investige further or to publish that info here.
What I understood so far is that you need plymouth (even though I do not need a splash screen, my receiver does not pick this screen up no idea why but for the moment I do not care).

I made a change in grub.cfg since sometimes the nouveau driver was wrongly blakclisted, this did not help.
I am also using the special xbmc script to make suspend work.

Besides the above problem I am wondering why under ubuntu my fan is always running in maximum speed. Is this because it is not using the speedstep tech of an Atom D525 or.... pwmconfig gives me the message it is autostepped!

Any help is greatly appreciated to make this work. For the rest ubuntu is running fine and is doing a good job even though I am not an experienced user.

---

