---
title: "Intermittent flashing black screen"
date: 2018-08-15
forum: General Help
---

### Post by cbmgraphics on 2018-08-15
[COLOR=#1C1C1C][FONT=&quot]Hola boys, I got a little issue. My screen flashes black for a split second and I have no clue why. Currently running a new install of Ubuntu 18.04.1. Got the necessary drivers from AMDs site (I'm running on a RX580) and all that. Thought at first it was something with Compton since I'm running that on this WM, although I loaded up the normal Ubuntu DE and it happens over there too. Any idea as to what's going on? It's an extremely mild inconvenience at best but nonetheless, I don't like knowing there's something going wrong in the background somewhere.[/FONT][/COLOR]

---

### Post by DuckHook on 2018-08-15
Welcome to the forums, cbmgraphics.

Not to belabour a point, but a significant contingent of Ubuntu Forum members are not boys. In fact, some of the gals in this forum can run rings around us guys when it comes to technical knowledge, quality of instruction and patience.

As for your question, the first step to diagnosis should be your logs. Try having a gander at them and look especially for errors dealing with your video card. You can grep dmesg to filter the output into more manageable proportions.

---

### Post by cbmgraphics on 2018-08-16
> **DuckHook said:**
> Welcome to the forums, cbmgraphics.

Not to belabour a point, but a significant contingent of Ubuntu Forum members are not boys. In fact, some of the gals in this forum can run rings around us guys when it comes to technical knowledge, quality of instruction and patience.

As for your question, the first step to diagnosis should be your logs. Try having a gander at them and look especially for errors dealing with your video card. You can grep dmesg to filter the output into more manageable proportions.

Looked through everything pertaining to AMD, gpu, warning, and error in dmesg. Nothing in there that looked wrong, next step? lol

---

