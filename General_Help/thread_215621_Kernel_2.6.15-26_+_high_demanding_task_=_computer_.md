---
title: "Kernel 2.6.15-26 + high demanding task = computer freeze"
date: 2006-07-14
forum: General Help
---

### Post by joe343 on 2006-07-14
Hi,

I upgraded to the last kernel (2.6.15-26-386) and everything went fine.  But when I run a task who requires a lot of CPU-I/O-memory, the computer just freeze (no more mouse/keyboard, and the screen freezes) and I have to do a reset on my tower.  The task I'm taking about is converting AVIs to DVD using Tovid.  Before that, with kernel 2.6.15-25-386, I had no problems.  Now I have to boot in 2.6.15-25-386...

Any idea where I shoul look ? I don't see anything interesting in my logs.

(Using Ubuntu 6.06 and the specs of my computer are in my signature)

Thanks

ps If I don't run the video convertion, everything works like a charm...

---

### Post by T700 on 2006-07-14
No terribly brilliant suggestions, but I have seen a similar situation fixed by increasing the swap space (assuming you are not in a position to add more RAM). 

Good luck,
Paul

---

### Post by joe343 on 2006-07-14
Hi, thanks for your suggestion.  I already have a 2gig swap partition. Plus, I rebooted in the last kernel (2.6.15-25) and I'm running the same exact task that made my computer freeze 4 times yesterday in the 15-26 kernel and I'm only using 37% of my ram.  The CPU is at 100% though.  I guess when the computer freezes, no logs are written right ? So I cannot have much clue of what's going on...

---

### Post by joe343 on 2006-07-14
Ok, now my computer just rebooted by itself while converting the AVIs.  But this time I was using DeVeDe instead of Tovid and I was using 2.6.15-25 so I don't think it's the kernel who make this happen...

Could it be the videos ?  Nothing appears in my logs so I'm kind of lost...

---

### Post by rbmorse on 2006-07-14
I think you power supply is inadequate or gradually degrading.

---

### Post by kripkenstein on 2006-07-15
It might also be a temperature issue. Monitor your CPU and motherboard temperatures, it could be that under heavy load they overheat, leading to instability.

(Or, try to run a heavy load with extra cooling applied.)

---

### Post by joe343 on 2006-07-15
I thing you guys might be right.  After a crash (computer reboots by itself), I checked the CPU temperature in the bios: 85 degrees celcius.  According to many websites about cpu temperature, my celeron 1.7 have a max of 67 to 77 degrees celcius - depending on model.  So is 8 degrees enough to cause a crash ?  What is it I can do about this overheating ?

Another question, in the bios, I have the cpu fan speed, which seems to be ok, but the system fan speed stays at 0.  Is it normal ?

Thanks.

ps Sorry about blaming my problems on the new kernel... just a coincidence !

---

### Post by Skye on 2006-07-15
I think that most modern CPU have a thermal shutdown feature- in other words, when the CPU gets too hot, it shuts itself down independently of the OS- think of it as a fail-safe.  But yes, it running at 85 Celcius is enough to trip the thermal shutdown by itself, and remember, that number is probably lower than the actual temperature because during boot, the CPU isn't running at 100% load.

As to your system fan being at 0, there's an easy way to check that.  Take the side of your case off, and check to see if your system fan, (which is usually mounted face out the back of your case) is spinning.  It's possible that the system fan just doesn't provide data information back to the mobo, but still spins fine.

If, when you open it up, it's covered in dust, you should invest in some compressed air to clean it out-  dust can make internal temperatures skyrocket, even if fans are working correctly.

---

### Post by Ramses de Norre on 2006-07-15
I'd clean out your case, all heat sinks and fans should be dust free and you could wipe all dust from the other hardware too.
If that isn't enough you might need to buy a stronger cpu cooler.

---

