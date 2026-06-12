---
title: "The ENTIRE system simply freezes randomly."
date: 2018-07-28
forum: General Help
---

### Post by vigdu on 2018-07-28
I started to use Ubuntu 18.04 about a week ago and from time to time the entire system freezes, normally when i'm using image manupulation programs like GIMP or Inkscape but it also crashes when I'm using my browser (Chrome) and I just don't really know what to do: I just turn off the computer manually in the cabinet.

AMD Ryzen 3 1200 
8 GB RAM
AMD Radeon HD 8600

---

### Post by Autodave on 2018-07-28
Is this a dual boot machine? If so, does the problem happen on the other OS? The system freezing could be software related, but it could also be hardware related.

---

### Post by vigdu on 2018-07-28
No. It isn't a dualboot machine
Until last week I was running Windows 10 in this machine, random freezes never occured. After I loaded up Ubuntu 18.04 from a pen-drive this started happening. The only 'hardware thing' that could be happening is when I opened up the pieces to build the PC and I accidentally touched the thermal paste for less than 1 second and since that is very unlikely I think it's certainly software that is causing the problem

---

### Post by HermanAB on 2018-07-29
In my experience, this kind of problem usually requires drastic action to find a fix: Upgrade the kernel/downgrade the kernel (from kernel.com)/install a completely different Linux distribution.

---

### Post by Autodave on 2018-07-29
I doubt that touching the thermal paste did anything, but you obviously had the chip out: are you that you properly reseated it?  If you didn't remove the chip, are you sure that it wasn't partially unseated when you pulled the fan off of it? This is interesting since you are doing rather CPU intensive stuff when it does freeze, so it *could *be a problem with the CPU overheating.

---

### Post by kurt18947 on 2018-07-29
> **vigdu said:**
> I started to use Ubuntu 18.04 about a week ago and from time to time the entire system freezes, normally when i'm using image manupulation programs like GIMP or Inkscape but it also crashes when I'm using my browser (Chrome) and I just don't really know what to do: I just turn off the computer manually in the cabinet.

AMD Ryzen 3 1200 
8 GB RAM
AMD Radeon HD 8600

That's interesting, what mother board?. I just refreshed a box with an Asrock AB350M MoBo & Ryzen 3 2200G. It wouldn't boot using the built-in GPU and this is a documented problem.  Knowing this, I installed a video card similar to yours - HD 8490 - I think. It booted up and is working fine, I've used it for probably 15 - 20 hours. If I uninstalled the video card and connected to the onboard video, the monitor would look like it had a video signal, the light would change but the screen stayed black. It would however display the splash screen and permit me to get into the BIOS, it just wouldn't boot. I don't know if this thread will help you or not but you might take a look:

[http://forum.asrock.com/forum_posts.asp?TID=7651&title=asrock-ab350m-pro4-freezing](http://forum.asrock.com/forum_posts.asp?TID=7651&title=asrock-ab350m-pro4-freezing)

One thread, don't know if it was that one or not felt that perhaps it was a power management issue, it looked to the poster like the PCI bus was powering down for no apparent reason. I think there's a way to disable power management editing GRUB but don't know how. If you don't have the most recent BIOS version, you could try updating that though I haven't seen many success stories from BIOS upgrades.

---

