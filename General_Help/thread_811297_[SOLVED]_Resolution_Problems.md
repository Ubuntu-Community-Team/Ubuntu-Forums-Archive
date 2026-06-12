---
title: "[SOLVED] Resolution Problems"
date: 2008-05-29
forum: General Help
---

### Post by Plasma_NZ on 2008-05-29
Ok, have a friend who uses... a Dell 24" 2405fpw

he uses resolution 1920x1200 and its stuck @ 50 herts..

its spec's for vert/horiz are

Max Sync Rate (V x H): 76 Hz x 81 kHz 

- can someone help with adding a modeline or something into the xorg.conf to achive at least 60hertz or better in the above resolution.?

---

### Post by Silpheed2K on 2008-05-29
I don't know much about using all that.. (the specs on the monitor) but that's what it's capable of and probably not what the actual videocard can handle/output.. (theoretically of course... of course i'm referring to the lowest end hardware just in case)
but what kind of videocard does he have? and does he have the videocard drivers installed? (can make a big difference in video performance i say)
if he doesn't have any videocard driver's installed I recommend he install them.
then try it.

---

### Post by Plasma_NZ on 2008-05-29
> **Silpheed2K said:**
> I don't know much about using all that.. (the specs on the monitor) but that's what it's capable of and probably not what the actual videocard can handle/output.. (theoretically of course... of course i'm referring to the lowest end hardware just in case)
but what kind of videocard does he have? and does he have the videocard drivers installed? (can make a big difference in video performance i say)
if he doesn't have any videocard driver's installed I recommend he install them.
then try it.

He has the latest NVIDIA driver's installed...

His card is a 7950GT - so it should be able to handle..

Just need to add some modelines and stuff to xorg.conf i believe..

---

### Post by frmneo999 on 2008-05-29
Try installing " NVIDIA X Server Settings" inside system tools in add/remove applications. 
After installation, go to system>administration> NVIDIA X Server Settings

Inside X Server Display Configuration , set the resolution and frequency. 

I had a similar issue, and it was solved by this way. I dont know if there is any easy way around..

---

### Post by Plasma_NZ on 2008-05-29
> **frmneo999 said:**
> Try installing " NVIDIA X Server Settings" inside system tools in add/remove applications. 
After installation, go to system>administration> NVIDIA X Server Settings

Inside X Server Display Configuration , set the resolution and frequency. 

I had a similar issue, and it was solved by this way. I dont know if there is any easy way around..

doesn't work, and i have the same problem with my lcd aswell etc.. im stuck @ 60 when i truely want 75..

---

