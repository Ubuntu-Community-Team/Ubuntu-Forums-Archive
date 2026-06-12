---
title: "can't enable normal, extra or custom effects after upgrade"
date: 2008-04-27
forum: General Help
---

### Post by westcoasteagles on 2008-04-27
Recently upgraded to 8.04 without too many dramas except.... 

Had 7.10 going nicely before the upgrade. Custom effects worked nicely.

After upgrade I haven't been able to enable the NVIDIA driver without it causing the system to lock up on boot (it hangs at the "Running local boot scripts (etc/rc.local)" line).

What info can I provide to help work this out?

thanks in advance
simon

---

### Post by akshar_patel_47 on 2008-04-27
Check the status of your Nvidia card proprietary drivers from system-> administration -> Hardware drivers. If it is enabled then disable it then restart your computer and then enable it again with your internet on so that the hardware driver manager can find the right driver for you.

If it is already disabled then enable it with your internet connection on.

Just try this out.

---

### Post by Zorael on 2008-04-27
If that doesn't work, open up Synaptic, find nvidia-glx(-new or -legacy), and pick **completely remove**. Then reinstall the packages. This'll fix things if there are remnants from old drivers left in your system.

---

### Post by westcoasteagles on 2008-04-27
thanks very much for he replies.

Unfortunately, I've given those suggestions a few goes - but no change I'm afraid... :(

---

### Post by Zorael on 2008-04-27
Were it me, I'd back up my home folder and then making a fresh Hardy install. Troubleshooting init scripts is sort of out of my league.

---

### Post by westcoasteagles on 2008-04-27
well, given I don't have an installation cd and there is no way i am going to bother trying using a burned installation cd again i guess i'll just have to settle for the basic graphics. They work at least.

cheers anyway

---

### Post by ssadhale on 2008-04-27
Well I like what Zorael suggested here. I didnt upgrade. I backed up everything on my 750 GB external hard drive and did a fresh install of Hardy. I had some many custom things on gutsy, that I didnt have enough confidence that the upgrade would come out clean. And then, fresh install has its own crispyness - like the smell of a new notebook at the beginning of new school year! what say? :)

---

### Post by westcoasteagles on 2008-04-27
can I say..."maybe that's not the way it is meant to work"? ;-)

---

