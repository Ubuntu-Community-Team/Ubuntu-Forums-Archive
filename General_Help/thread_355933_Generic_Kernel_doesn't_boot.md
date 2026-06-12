---
title: "Generic Kernel doesn't boot"
date: 2007-02-07
forum: General Help
---

### Post by ZeldaFan on 2007-02-07
I just installed Edgy Eft on my HP dv9000t laptop, which uses a Intel Core 2 Duo 1.83 gHz processor. However, when I want to run the generic kernel in Edgy, it almost never ends up booting. It booted successfully once or twice (and also utilized both of my cores in my processor) but besides that, the boot freezes up when the boot up bar is around the middle. The 386 kernel works fine, but the only problem is that it doesn't recognize both of my processor's cores. Are there any alternative kernels or any solutions to this problem?

---

### Post by DagMan on 2007-02-07
If you don't find the solution elsewhere, It might be helpfull if, when you're at the grub menu while booting, you hit the letter e on the keyboard (escape first if you have a hidden menu) then use the arrow keys to select the line that begins with kernel, then hit the letter e again.  Then use the arrow keys to go to the very end of this line.  The end of the line might be off of the screen.. just keep going until you get there.  delete the word splash, hit enter, hit the letter b on the keyboard, and you will boot without the splash screen.  Then you'lle be able to read what it says when the boot process stops.

I probably can't help with whatever the output is but someone else might be able to... if the problem isn't solved some other way, I don't have a core 2 processor so I havent been reading about anything relating.

---

### Post by wislon on 2007-02-09
Zeldafan, I have the same problem. i386 boots just find, but no dual-core support. I tried booting to generic and I get zip zero nada. I even left it for 5 minutes (several times) to see if it would come back on its own. It never did.

DagMan, I'll try removing the splash screen as you suggested, good idea! :)

---

### Post by ZeldaFan on 2007-02-09
Actually I don't think I ever had a problem, because I just let the kernel boot for a couple more minutes and it eventually loaded. I never had to do any other tweaking or anything.

---

### Post by Toufik on 2007-02-10
Fill a bug at launchpad ([https://bugs.launchpad.net/ubuntu/+bugs](https://bugs.launchpad.net/ubuntu/+bugs)) there are already many reports of problem with generic kernel, so look first if yours is already described.

Toufik, nearly the same problem as yours...

---

### Post by wislon on 2007-02-10
DagMan, your suggestion worked. I turned off the 'splash' and 'quiet', and discovered that a suggestion I had made to someone else in another thread applied to me too. 

Ever since I've installed Edgy, it kernel panics on startup (something about a sync problem) unless I use the  boot parameter 'acpi=force'. 

As soon as I saw the error, I knew how to fix it. I edited my grub menu, added the parameter, and voila! I've made the option permanent in the grub boot params. This does of course mean I'll get burnt by it MONTHS from now, when I've forgotten all about it :)

---

