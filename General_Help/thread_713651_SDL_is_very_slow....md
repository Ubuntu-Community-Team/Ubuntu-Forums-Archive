---
title: "SDL is very slow..."
date: 2008-03-03
forum: General Help
---

### Post by Oen386 on 2008-03-03
I am wondering if there is any way to see why SDL is running slow. I can only assume it is my graphics card (Radeon 9800). I use to play a game with SDL (SimuTrans on 7.04 Feisty) and the speed was fine. I have recently checked out other games (while using a fresh install of Gutsy) and any games I try to play runs really really slow (as in like 1 frame every 3-5 seconds). An example would be Super Maryo Chronicles (the menu is too slow for me, I  move my mouse and it takes 5 seconds for the movement to show).

Is this graphic card related, are there any tests I can run to find the issue? Maybe I need to update something? Thanks.

---

### Post by myand on 2008-03-28
Hi,

I have a Radeon 9600 and had the same issue with Super Maryo Chronicles. I was able to resolve it by installing DriConf (the 'driconf' package) and adding an SMC-specific Application Setting (Executable Name smc) rule to "Disable Low-impact fallback". The game seems to work okay now apart from the sound which is crackling like it was coming from an old vinyl recording (dunno if that's intentional though), although at least on one occasion it froze my desktop and I had to resort to Ctrl+Alt+Backspace.

---

