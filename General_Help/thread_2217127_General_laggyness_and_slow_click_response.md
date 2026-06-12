---
title: "General laggyness and slow click response"
date: 2014-04-15
forum: General Help
---

### Post by terrykiwi83 on 2014-04-15
Greetings all,

Was hoping to shine some light on a little problem I have. So recently I have just installed 13.10 x64, and it seems very laggy. Reasons below:

1. When I click on something in the launcher it takes about 10-20 seconds to start.
2. Sometimes they take over a minute.
3. The sound works, however, there is no sound icon up the top right?

The specs of my system:

Intel i7 3770
16GB DDR3 RAM
1TB HDD
Intel HD4000 GFX
Onboard Sound

Cheers for any advice.

Terry

---

### Post by grahammechanical on 2014-04-15
You may be loading with the Ubuntu fallback video mode. Go to System Settings>Software and Updates>Additional Drivers tab and experiment with another video driver. You will need to wait several seconds for the Utility to come up with a selection of video drivers.

Something to keep in mind, if a video driver fails to load Ubuntu to working desktop is that at the Grub boot menu we can select Advanced Options for Ubuntu and then select Recovery mode. At the Recovery menu if we select Resume, then Ubuntu should load using its fallback video that I think is running right now on your machine.

Regards.

---

### Post by terrykiwi83 on 2014-04-17
Thanks for the reply. I have checked in and my system has no additional drivers. Doesn't even offer a list.
I am not running in the recovery mode either, I did try that route to see how it would work and still laggy :(

Any other ideas?

---

### Post by tgalati4 on 2014-04-17
Open a terminal and post the output of:

```
w
```

---

### Post by terrykiwi83 on 2014-04-20
> 
terry@AOC-PC:~$ w
 18:12:42 up  1:59,  2 users,  load average: 1.19, 1.28, 1.23
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
terry    :0       :0               16:15   ?xdm?   3:42   0.10s init --user
terry    pts/0    :0               18:12    1.00s  0.02s  0.00s w
terry@AOC-PC:~$ 


Also I should mention I have no sound at all now. Randomly just decided to vanish.

I have also upgraded to Ubuntu 14.04 x64 and the laggyness is still evident, just not as bad.

---

