---
title: "Memory leak issue 13.10"
date: 2013-11-08
forum: General Help
---

### Post by speartip on 2013-11-08
I know this was mentioned in a previous thread. But can anyone tell me if the memory leak issue on Ubuntu 13.10 has been resolved yet?
The one where everytime you open the dash, compiz steals about triple the memory, & I think the package unity-scope-home eats up about 500mb of my 3.5gig.
 I reinstalled 12.04lts until this problem is resolved. Would appreciate any recent feedback.

---

### Post by speartip on 2013-11-26
I know noone replied to this thread, but even a month after release and a fresh install this is still an issue for me.
I am sure unity-scope-home is the culprit, according to system monitor, & compiz quickly follows suit, eating up large amounts of memory.
Logging out & back in again releases the memory, but I don't want to have to do this everytime I invoke the dash.
Am I the only one with this issue, or is anyone else noticing this?

---

### Post by andrew-n1by9anq9 on 2013-12-06
I still seem to hit it. Rather than having to log out and back in though you can send a HUP signal to compiz. This will move all your windows around and possibly take some time to return control but your processes remain running and it seems to improve things performance and memory wise. YMMV.

I try to remember to do this every time I dismiss the screen saver as that mucks up window placement as well so I will already have to go searching for them.

---

