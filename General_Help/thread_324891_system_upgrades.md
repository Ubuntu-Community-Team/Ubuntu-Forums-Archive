---
title: "system upgrades"
date: 2006-12-24
forum: General Help
---

### Post by billklee on 2006-12-24
I've got a Shuttle XPC, running Edgy. 2.8 GHz P4, 512 MB RAM, 300 GB IDE HD. I've moved to this from a 500 MHz PowerBook, yet at times, this seems to be no faster. Firefox/Swiftfox seem to be the worst offenders: they're the programs that most often bog down, and terminating Swiftfox increases free memory from 6 meg to about 120. What gives here? Is there a way to prevent this, or should I be looking at the other browsers closer?

I already know I need more RAM (running free tells me I've got 6 MB of Free RAM), and I've ordered 2 GB to max that out. I believe this is the single largest bottleneck I've got, but I could be wrong.

I'm thinking of getting a video card, instead of using the on-board video. I'm looking at an EVGA GeForce 4000 (it's cheap, and I don't game). Will this make a noticeable difference? I notice that this card has both PCI & AGP versions; I assume AGP is "better" or at least faster.

I'm also thinking about adding a SATA hard drive for /, and keeping /home on the IDE drive. Would that make a noticeable difference, and if so, how large of a drive would I need? 20 gig? 40 gig? And if I do that, is there a way to migrate the existing install to the SATA drive and set the IDE up as /home, without having to reinstall everything?

What other things can I do speed it up, or at least keep it from stopping to catch its breath?

Forgot to ask: will I need to increase the size of the swap partition after adding more RAM? I know that a lot of people claim that you don't really need a swap with >1 GB of RAM, but if I'm going to do it, I want to do it right. If I need to bump the swap up what's the best way to do so?

---

### Post by d.j.schroeder on 2006-12-24
Definitely the video updrade will make a difference.  AGP is faster than PCI, make sure you have an AGP slot not a PCI-express slot (I have a P4 board with similar specs that is actually PCI-express). 

About the rest I can't say, though 2 GB sure seems like more RAM than you would really need.

---

### Post by billklee on 2006-12-24
According to the mobo book, I've got 1 AGP slot and 1 PCI slot. I figure that if I use AGP, it'll leave the PCI open for future expansion, but if I go PCI, what can I put in the AGP slot later but a video card?

I've always believed that more RAM is better. Besides, I found a heck of a good deal.

---

### Post by tenghoward on 2006-12-24
> **billklee said:**
>  what can I put in the AGP slot later but a video card?

Umm... AGP (Accelerated Graphics Port) slot is for video cards only. :-k

---

### Post by billklee on 2006-12-24
Like I said, "what can I put in the AGP slot later but a video card?"

---

### Post by tenghoward on 2006-12-24
> **billklee said:**
> Like I said, "what can I put in the AGP slot later but a video card?"

I can't think of anything else than video cards. Also, which Ubuntu version you are using? Ubuntu and Xubuntu are pretty light weight. :confused:

---

### Post by billklee on 2006-12-24
> **tenghoward said:**
> I can't think of anything else than video cards. Also, which Ubuntu version you are using? Ubuntu and Xubuntu are pretty light weight. :confused:

Edgy K/X/Ubuntu, as the mood takes me.

---

