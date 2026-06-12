---
title: "Batterycontrol / Feisty"
date: 2007-04-24
forum: General Help
---

### Post by ignorance on 2007-04-24
I recently updated my edgy to feisty and got no problems at all that is for one little thingy. The battery-life of my laptop HP NX 7400. It only lasts for about one hour and 45 minutes. I know that the laptop has an battery life of 2.5 - 3 hours under windows. Is there a way to make the battery last longer and a more resolute battery monitoring system? Since the one i'm using Power Management (Gnome thing i think) isn't really accurate.

Cheerz

---

### Post by strabes on 2007-04-24
My laptop's battery life also suffers under linux as compared to windows. This is something that I have just grown to live with. However, it will only get better with time and with new kernel releases.

---

### Post by hardyn on 2007-04-24
There is actully quite a bit that you can do... well some anyway :)

there is a hidden laptop-mode, if you search for my posts, i have done this exact post before... it required goofing around with some files, it changes the CPU throttle and spins down the hard disk after X seconds.  that will be good for a few minutes (30ish)

there are some threads on forcing the wireless cards into power saving mode, but currently linux doesn't play nice with these maybe feisty +1? 

don't use the NV or ATI video drivers, they are designed for desktop boards (of course) and run the GPUs pretty hard, and both the radeon and fglrx have power saving modes, nvidia-glx does not.

there have been some uplifting grumbings about kernel 2.6.21, it may be offering better cpu management.

i don't know if this will get better overtime with out us, the laptop users, being a little more vocal.

cheers.

---

### Post by ignorance on 2007-04-25
I'll search for that. Anyone else got some idea's?

---

### Post by dhruva023 on 2007-04-26
i have the same problame,

my battery life goes down when i boot up ubuntu, also my cpu gets hot.

is there any idea how to fix this?

---

