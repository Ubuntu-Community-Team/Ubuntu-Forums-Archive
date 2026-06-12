---
title: "Weirdness in Java/Azureus"
date: 2005-06-19
forum: General Help
---

### Post by Krank on 2005-06-19
Up until recently, I was a moderately happy user of Azureus and aMule.

Suddenly, my graphics card upped and died on me, so I changed to the motherboard on-board graphics card, and reconfigured X to use the new config.

So far, everything worked.

But, for some reason, this little operation completely fouled up both Azureus and aMule. Azureus was always a darn resource hog, but Java didn't use to hog 330+ mb of RAM while I was using it - not 'till today.

Same deal with aMule. It's not as bad, but it used to be hogging a mere 5-10% of the processor, but now it's somewhere between 10% and 25% - of the same processor.

I should not need to reinstall the whole system just to get these two progs working - any ideas?

---

### Post by diebels on 2005-06-19
Bet your onboard graphics card has no ram onboard and eats up system ram. Setting DefaultColorDepth to 16 if it's currently 24, could help.

---

### Post by Krank on 2005-06-20
OK, I just solved the mystery. I noticed that the gnome-system-monitor for some reason only showed that I had 64 mb RAM, while it was my understanding that I had 512+32+32. I checked during bootup, and indeed - BIOS showed only 64 mb RAM, it basically refused to find my 512 mb.

A few simple experiments later, I find that my 512 does work, but only, for some inexplicable reason, when the two 32-mb-ram's aren't connected... So, faced with the choice of 64 or 512 mb RAM, I of course chose 512, vowing to myself to one day purchase a new motherboard and RAM for my dear server.

---

