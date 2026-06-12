---
title: "ATi 7500 mobile and Desktop Effects will not work properly"
date: 2008-06-18
forum: General Help
---

### Post by Vegabondsx on 2008-06-18
Greetings,

I have a Compaq Evo with a 32mb 7500 mobile video card.

I have been unable to get Desktop Effects working properly.

When I go to select "Normal" or "Extra" under affects I get an error saying Desktop Effects could not be enabled.

I found a way to have Ubuntu ignore this and enable it anyways, but the performance is horrible and slow. I have gotten Desktop effects to work on an Intel 900 and nVidia GeForce 2 and performing well. I'm guessing this is due to drivers. Unfortunately ATi's current drivers don't support the 7500. Anyone know on how to get proper drivers for this card so I can at least get the normal effects working properly?

Thanks,
Ryan

---

### Post by Rocket2DMn on 2008-06-19
Have a look at this thread - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
I think most people using that card have at least been able to get compiz to run, though performance may suffer a bit because of how old the card is.

---

### Post by talkingwires on 2008-06-19
Check out the [thread pinned to the top of this forum](http://ubuntuforums.org/showthread.php?t=765875). The 7500 has been removed from a "white list" of chips that can run Compiz, mostly because the developers didn't want to go to all the trouble of fixing a bug. Block a bunch of chips that are only supported by an open source driver and can run Compiz just fine because of a problem with just one of them, problem solved.

I have the same graphics chip in my laptop; it runs fine when you disable the the white list, as described in the link above.

---

### Post by Vegabondsx on 2008-06-19
> **talkingwires said:**
> Check out the [thread pinned to the top of this forum](http://ubuntuforums.org/showthread.php?t=765875). The 7500 has been removed from a "white list" of chips that can run Compiz, mostly because the developers didn't want to go to all the trouble of fixing a bug. Block a bunch of chips that are only supported by an open source driver and can run Compiz just fine because of a problem with just one of them, problem solved.

I have the same graphics chip in my laptop; it runs fine when you disable the the white list, as described in the link above.

This allows Compiz to be used, but the performance is poor. Is this what you experienced? It seems like the GeForce 2  I have on a slower machine runs better.

---

### Post by talkingwires on 2008-06-19
> **Vegabondsx said:**
> This allows Compiz to be used, but the performance is poor. Is this what you experienced? It seems like the GeForce 2  I have on a slower machine runs better.I haven't found enabling it to cause any slowdown. This is on a Dell c640 laptop, and the chip has 32Mb of dedicated memory.

However, a quirk has appeared in Hardy's version of Compiz: maximized windows' borders turn white.

---

