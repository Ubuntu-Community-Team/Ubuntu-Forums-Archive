---
title: "Is there an application that will allow me to use an old laptop as a second monitor?"
date: 2015-07-08
forum: General Help
---

### Post by kylesmail80 on 2015-07-08
Both my desktop and laptop are running Ubuntu 14.04 and I want to be able to click and drag application windows from my monitor to my laptop wirelessly (like a second monitor)

---

### Post by sandyd on 2015-07-08
From what I can see, you can either

1. Use xdmx (Side note, documentation is hard to find ever since it got merged into Xorg, the most recent person who got it sort of working is at [here]("http://www.spinics.net/lists/xorg/msg56256.html"))
2. Create a second Xorg display (0:1), and use VNC on the second computer. You can then use Xorg and Xinerama to extend display. Haven't tested it, but it may be possible to use x2go with it.

---

### Post by tgalati4 on 2015-07-09
You can install *synergy* and use one mouse to control actions from both over the network.  Not exactly pulling apps across, but it gives you additional desktop functionality.

---

