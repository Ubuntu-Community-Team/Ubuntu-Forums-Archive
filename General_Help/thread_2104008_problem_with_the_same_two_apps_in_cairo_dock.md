---
title: "problem with the same two apps in cairo dock"
date: 2013-01-11
forum: General Help
---

### Post by firekage on 2013-01-11
Hi.

I would ask for your help. I upgraded my Ubuntu 12.04 to 12.10 and since upgrading i have problem with cairo-dock.

On Ubuntu 12.04 when i had launched two the same apps i could point mouse to them and click the one i want to shown/use.

This behaviour was fine but after upgrading to 12.10 it doesen't work just like it used to be. When i have two the same apps lanuched, and i point the mouse on them in order to choose one of them than i;m not able to choose any of them because right when i point mose a little to high (in order to choose one of the two the same apps) than cairo-dock disappears, hides, even when cairo-dock panel is set to not autohide.

Is there a bug, or is there a fix for it? I tried to 

aptutude purge cairo-dock

aptitude install cairo-dock

but in fact this doesen't helped at all because after rebooting all my cairo-dock set up was stiil there, it weren;t purged at all with aptitude (maybe i should do it just like i always did, with apt-get --purge remove?) - it is not a big problem, i can do it later.

The problem is one : is this a bug, or is there a fix for it?

I have two screens, look at them.

On screen one i have two terminal running. On screen two i want to choose one of them (red line shows how high i place mouse) and when i should choose one of them, cairo-dock hides / running away and i'm not able to choos (my temporary solution is to use docky....bo i like cairo dock, it worked on 12.04, now it doesen't on 12.10).

Could you help me?

---

### Post by firekage on 2013-02-04
Anybody?

---

### Post by firekage on 2013-02-04
I fixed this, problem solved.

I tried to reinstall it with aptitude and apt-get. Still no luck, even with purge options. Strange for my is that "purge" should really purged all, also with user settings. I think not...

I had to use aptitude with purge but also delete everything from ~/.config/cairo-dock and everything regarding cairo-dock.

After this i installed it again with aptitude and it works. Now i can have the same apps opened, than i can minimize it and bring it back without cairo-dock running away while i put my mouse over item that was few times opened.

---

