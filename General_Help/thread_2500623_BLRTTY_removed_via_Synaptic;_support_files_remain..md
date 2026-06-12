---
title: "BLRTTY removed via Synaptic; support files remain."
date: 2024-09-06
forum: General Help
---

### Post by ozark_hillbilly on 2024-09-06
Ubuntu 22.04 LTS

I removed the blrtty app through Synaptic Package Manager. 
It was interfering with the USB port used by the Arduino IDE app.

Upon removal Synaptic informed me /var/lib/BrLAPI was not empty
so it was not removed.

It removed blrtty and libbrlapi-dev [support file].

It also left behind:
   
libbrlapi0.8
python3.brlapi
xbrlapi

My question is can I safely remove these other 4 support files without creating any OS issues?
I can leave them alone, its just that I like to make removals as clean as possible.


...synaptic screenshot attached....

thanks....

---

