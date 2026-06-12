---
title: "computer screwed up after power-outage"
date: 2008-05-19
forum: General Help
---

### Post by Detox06 on 2008-05-19
So I guess the power went out about 10 last night right before my girlfriend came to bed. Well this morning when I log on, my /dev/sdb and /dev/sdc drives are gone. I can't find them in Nautilus, and I can't find them with gparted. Also when I installed gparted, it didn't go onto my menu like it was supposed to, it just kinda isn't anywhere and I have to start it from terminal. I have a lot of my movies on my sd(x) drives and really need to get them back. Can anyone help me out? 

Also as a side note, I'm using a 42" TV as my monitor, and when I log in I'm getting some sort of message (unrelated I'm sure because I've been seeing the message for a couple days now) but can't read it because it doesn't scale up. Res is set at 1024x768 and I can read everything but that message. My username doesn't show up very well either, but the word 'Username' and 'Password' above the box show up fine. Help? 

Ubuntu 8.04 on an AMD3500+, 1gb RAM, sd(x) are located on a sata expansion pci card.

---

### Post by sdennie on 2008-05-19
Does your BIOS show all your drives?  It's possible (though, I don't know how likely) that your power outage has damaged your SATA card.

---

### Post by Detox06 on 2008-05-19
I don't know how likely it is, but that seems to be exactly what happened. After I posted, I changed my /dev/sdb from the sata card to my other onboard sata port that's so far been empty and it works just fine. So its either the card or the slot. I can't check the slot until my gf wakes up, but if it is the slot, shouldn't it have affected my soundcard and gfx card as well since they are on pci/pci-e slots? 

Oh well. If it's my card, a new one is only like $14, and if its the slot, I've been meaning to build a new computer anyway. Maybe this is just the push I needed...

---

### Post by sdennie on 2008-05-19
> **Detox06 said:**
> I don't know how likely it is, but that seems to be exactly what happened. After I posted, I changed my /dev/sdb from the sata card to my other onboard sata port that's so far been empty and it works just fine. So its either the card or the slot. I can't check the slot until my gf wakes up, but if it is the slot, shouldn't it have affected my soundcard and gfx card as well since they are on pci/pci-e slots? 


It's not really possible to say.  If the power outage has done damage to your system I don't think you can predict how it's done it.

> 
Oh well. If it's my card, a new one is only like $14, and if its the slot, I've been meaning to build a new computer anyway. Maybe this is just the push I needed...

I would also invest in an UPS of some sort.  I think "power strips" only protect in the event of some massive power surge whereas a decent UPS will actually send you "cleaner" electricity even under questionable presence of electricity.

---

### Post by Detox06 on 2008-05-19
I was actually thinking about this thing my uncle has, it may be a UPS I'm not sure. Its a 10 outlet big as crap box, and it has a built in battery backup of like 4 hours which would usually at least give me time to power off my box (or my gf if I'm asleep)

---

### Post by sdennie on 2008-05-19
> **Detox06 said:**
> I was actually thinking about this thing my uncle has, it may be a UPS I'm not sure. Its a 10 outlet big as crap box, and it has a built in battery backup of like 4 hours which would usually at least give me time to power off my box (or my gf if I'm asleep)

Yes, that's an UPS.  Most of them can also be setup to shutdown your computer automatically when the power is out and the UPS detects that it's about to run out of batteries.

---

### Post by ibuclaw on 2008-05-19
Wouldn't a Surge Protector have the same effect of preventing this sort of screwup too?

If so, could be a good cheap alternative.

Regards
Iain

---

### Post by Detox06 on 2008-05-19
Good good. I'll take a look when I'm out at Fry's today. Because at about 5 hours per dvd, and 150 dvd's stored, that would take months to re-rip if my drives were to fry.

---

