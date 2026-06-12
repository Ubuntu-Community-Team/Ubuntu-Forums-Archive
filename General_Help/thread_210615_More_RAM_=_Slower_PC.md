---
title: "More RAM = Slower PC?"
date: 2006-07-07
forum: General Help
---

### Post by paul.maddox on 2006-07-07
Hi,

Recently bought a Thinkpad T60 as my new work laptop which came with 512MB ram. I've been using it for a while now with XGL installed and it all ran very well looked sweet.

The only time I noticed the performance lagging was when I have a lot of applications open, so I just bought a 1GB stick of RAM to go alongside the 512MB I already have.

Unfortunatly now the laptop has 1.5GB of ram, it's dog slow when it comes to XGL. The cube desktop switcher is really laggy and jerky, other XGL effects have also got jerky all of a sudden!


What is going on? I don't understand!

---

### Post by Rui Pais on 2006-07-07
hi,
maybe a broken ram stick?

did that happen if you use only the 1GB RAM stick?

---

### Post by jongkind on 2006-07-07
Is the memory clockspeed of the new stick the same?

Furthermore, I think that new memory must be installed in pairs, e.g. 2x512 Mb.

---

### Post by TheMono on 2006-07-07
This may well be a stupid comment, because I don't know anywhere near enough, but could it be to do with HighMem support in the Kernel?

---

### Post by paul.maddox on 2006-07-07
I've played around with this a bit more now, I have now taken out the 512MB put in 2x brand new matched 1GB 667MHz (same speed as original RAM) sticks.

Even with 2GB of matched/paired memory XGL is more jerky than my original 512MB.

A work collegue mentioned this highmem kernel option, is this not enabled in ubuntu? 

/me goes away to google this highmem option

---

### Post by Rui Pais on 2006-07-07
hi again,
defaults ubuntu is CONFIG_HIGHMEM4G=y
so you have nothing to worry about that, either with 1 or 2 sticks of 1G in. 

i read somewhere that normally after 512M of ram you won't win much adding more ram on Linux, except waste power, but i'm not sure if thats true (should not be if you edit prof photos or video, at least)... but in anycase there a deep diference between not make any diference and slow it down like you are experience at your computer :(


Do you checked if your bios settings matchs the speed of the new sticks?

---

### Post by jlukar on 2006-08-25
I have the same problem. Upgraded my T60 to 2GB and it seems slower. the BIOS setting sees the memory and I don't see anything that allows me to set the memory stick speed.

the core dual setting support in bios is also enabled. So not sure what is going on.

uname says:  2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux.

anyone has any ideas why my system seems still slugish after upgrading to 2GB of memory ?

thanks


> **paul.maddox said:**
> Hi,

Recently bought a Thinkpad T60 as my new work laptop which came with 512MB ram. I've been using it for a while now with XGL installed and it all ran very well looked sweet.

The only time I noticed the performance lagging was when I have a lot of applications open, so I just bought a 1GB stick of RAM to go alongside the 512MB I already have.

Unfortunatly now the laptop has 1.5GB of ram, it's dog slow when it comes to XGL. The cube desktop switcher is really laggy and jerky, other XGL effects have also got jerky all of a sudden!


What is going on? I don't understand!

---

### Post by az on 2006-08-25
What if you use an optimised kernel like 686 for pentium/Celeron or k7 for AMD?

sudo apt-get install lnux-686

Any difference?

---

### Post by ifokkema on 2006-08-26
> **paul.maddox said:**
> I've played around with this a bit more now, I have now taken out the 512MB put in 2x brand new matched 1GB 667MHz (same speed as original RAM) sticks.

Even with 2GB of matched/paired memory XGL is more jerky than my original 512MB.

A work collegue mentioned this highmem kernel option, is this not enabled in ubuntu? 

/me goes away to google this highmem option

Just to completely rule out we're off the right track here - try putting back in the 512 by itself and test again. Fast as before? OK, we need to look into the memory thing. Still sluggish? Something else changed.

---

### Post by viciouslime on 2006-08-27
Since there are two of you with the same problem on the same laptop maybe it is a bios issue, have you both got latest bios?

---

### Post by peabody on 2006-08-27
It totally would not surprise me if this was a compiz/xgl thing.  Maybe they've optimized it for 512 megs of ram.  There might be a setting you have to set for Xgl or compiz.  This software is extremely touchy.  How is performance when you're not in XGL/compiz?

---

### Post by paul.maddox on 2006-08-27
To be honest, my laptop seems to have sorted itself out.

I still have 2GB RAM installed in it, and XGL+Compiz etc works fine now. No jerkyness in sight anymore!

No idea what it was, maybe an update or something.

I am using a 686 kernel by the way.

---

