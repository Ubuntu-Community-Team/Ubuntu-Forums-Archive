---
title: "Catalyst 13.2 beta 7 issue"
date: 2013-03-05
forum: General Help
---

### Post by jdbeitz on 2013-03-05
Hey guys.. first post!

So I upgraded my driver from catalyst 13.2 beta 6 to 13.2 beta 7 using the --force command on the .run file.  Now when i boot, I just see a black screen with a solid cursor.  I can't get into the command line and the cursor does not even blink.

Ubuntu 12.04 64 bit up to date as of yesterday
Radeon HD 6670 video card

What should I do to reisntall the old drivers without having to do a wipe on the pc?

help! 

Thanks!

---

### Post by Mark Phelps on 2013-03-05
According to the Release Notes from the AMD site, the 13.2 Betas are intended to work with the following:

> The AMD Catalyst&#8482; 13.2 Beta Driver for Linux is designed to support the following Linux distributions:

        Red Hat Enterprise Linux suite 5.7, 5.8, 6.2 and 6.3
        SUSE Linux Enterprise 10 SP4 and 11 SP2
        OpenSUSE 11.4 and 12.1
        Ubuntu 12.10 

Notice it says 12.10, not 12.04.  12.10 has a newer X-server version than does 12.04.

My guess would be that they "fixed" something in the latest beta that now prevents it from working with the older X-server version in 12.04.

---

### Post by jdbeitz on 2013-03-05
Thanks for the prompt reply. I quit using 12.10 because of how unstable it was. But I'll give it another whirl! :) thanks!

---

