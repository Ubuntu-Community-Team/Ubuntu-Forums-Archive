---
title: "Can't Boot into Ubuntu 6.10 (Edgy)"
date: 2006-11-20
forum: General Help
---

### Post by BuLLeTz on 2006-11-20
Hello

I have downloaded the AMD64 distro, since my processor is an AMD64, and when I get to the part where its just about to load into the Ubuntu GUI I get stuck at a black screen. 

My specs are as follows:

AMD Athlon64 3200+ 2.2GHZ Processor
1.50GB of DDR Ram
ATI X800XL 256MB Graphics Processor

If anyone has any suggestions as to get around this or as to why this is happening that would be great.

---

### Post by smoker on 2006-11-20
sounds like it is having problems with your graphics card, is there an option on the cd to use a safe/recovery/ mode, or to start with a basic standard driver? if so try this, you can always get the correct drivers when you have unbuntu up and running

---

### Post by BuLLeTz on 2006-11-20
I have tried booting into Ubuntu with the Safe Mode option on the CD, and it seems I am getting to the same spot, and encountering the same problem. :(

---

### Post by aparsons on 2006-11-20
Try using the alternative installation CD.  That worked wonders for me.

---

### Post by TLE on 2006-11-20
There is a flaw in the safe graphics mode. So when you ask it to boot in safe graphics mode it doesn't actually do so. There is a workaround for it [here]("https://wiki.ubuntu.com/EdgyKnownIssues/59618") it is a little complicated so if you get into any problems don't hesitate to ask. But I agree with smoker that this sound like a graphics card issue, so this should work
Regards TLE

---

### Post by BuLLeTz on 2006-11-20
Thanks for suggestions. I'll give this a try.

---

### Post by BuLLeTz on 2006-11-20
Alright, I tried what was suggested in that article you posted TLE. Everything seems to be going alright but just as its about to go on to the Ubuntu GUI with safe mode, my monitor goes dark and the green light begins to flash, however I can hear the Ubuntu startup music in the background. 

Its progress.

---

### Post by TLE on 2006-11-21
Is it a flatscreen? It might be a matter with the refresh frequencies. I think I have seen subject like that before.

---

### Post by BuLLeTz on 2006-11-21
No, my monitor isnt a flatscreen.

---

### Post by BuLLeTz on 2006-11-21
Bump

---

### Post by TLE on 2006-11-21
You made it stop in the boot process and made it use vesa in stead of your usual driver ?

Also. When you say that the green light starts flashing. Does that mean that your screen is on stand by?

---

### Post by BuLLeTz on 2006-11-21
Yeah. By following the instructions in that wiki article you posted, I was able to make it use vesa. 

And yes, when the green light starts flashing its like my monitor is on stand by.

By making it use vesa rather than my usual driver it seems to boot into Ubuntu, however my monitor is stuck on what looks to be stand by.

---

### Post by TLE on 2006-11-21
Can you get to a virtual terminal by pressing ctrl-alt-f1 ?

---

### Post by BuLLeTz on 2006-11-21
No. When I press ctrl-alt-f1 my monitor continues to be on "stand by". One thing I noticed in the xorg.conf file is that under the Device section where my video card is listed, it calls it PCIe, however, my video card is actually AGP. Could this mean anything?

---

### Post by TLE on 2006-11-21
Could be, but I must admit it is a little out of my league. I actually own a X800XL myself and I has given me problems. But for me problem has always just been that the standard drivers don't work, so I could just use safe graphics and install some other drivers. But anyway the bottom line is that I'm afraid I can't help you. I hope someone else will chime in.

---

### Post by BuLLeTz on 2006-11-21
Well, thank you none the less. It looks like the problem now has something to do with my monitor. I'll ask around. Hopefully others can give their input as well.

Thanks again.

---

