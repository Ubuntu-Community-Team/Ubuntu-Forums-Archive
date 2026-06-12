---
title: "No Video Hardy Heron"
date: 2008-04-27
forum: General Help
---

### Post by Valpatine on 2008-04-27
I installed the latest release of Ubuntu yesterday then I used Wubi to dual boot both Windows Vista and Ubuntu. It starts up just fine but I want to use desktop effects and play around with the software so I first go to restricted drivers and enable them, which then begins the download. Everything goes fine and I reboot, but after the initial loading screen no video is present! I had had this problem with 7.10 and I was really hoping this problem would be fixed in 8.04 yet it wasn't. I then reinstalled with Wubi and this time used EnvyNG rather than the restricted driver manager, still when I rebooted I had the same problem. My video card is a 8600gts and I would really like to begin using Ubuntu. I wanted to tinker with Ubuntu in Wubi (which is rather safe) so that I would focus on studying and preparing for my finals, then after finals week I was planning on reformatting my computer (something I had been planning on doing for awhile anyway, Ubuntu 8.04 just made me seriously consider) and dual boot XP and Ubuntu, so any help would be appreciated to solve this problem!

---

### Post by Valpatine on 2008-04-27
Bump.

---

### Post by eunit on 2008-04-27
I am having the same problem but mine relates to monitor resolution problems because the nVidia driver doesn't recognize my monitor at all.  Are you getting an "Out of Range" message from your monitor or anything?

---

### Post by Valpatine on 2008-04-27
> **eunit said:**
> I am having the same problem but mine relates to monitor resolution problems because the nVidia driver doesn't recognize my monitor at all.  Are you getting an "Out of Range" message from your monitor or anything?

No, mine just says "No Video".

---

### Post by seted on 2008-04-28
I am having a similar problem.

After enabling restricted drivers for my nvidia 8800GT I rebooted. After the initial looading screen completes, the screen goes black and the monitor shuts down. My keyboard doesn't respond either.

I had the same problem in Gutsy and hoped that upgading to Heron would help.

EnvyNG doesn't help.

I don't know if there is a problem with my card, or with my monitor, or if it is the Nvidia drivers.:icon_frown:

---

### Post by Mr Frosti on 2008-04-28
It sounds like the default driver behavior for nVidia might be to not clone your computer's display. I would recommend installing the nVidia drivers from nVidia's website. Its not as hard has you might guess thanks to really good Linux support from their company. 

With the "official" driver installed see if you get this same result. It could be a problem with the Ubuntu specific package of the nVidia driver.

Please look at the file "/var/log/Xorg.log" to see if any entries contain an "(WW)" warning, or an "(EE)" error. This can be accomplished by (1) choosing the recovery mode in the boot options (when it says to press "Esc" for additional options), or (2) from a virtual terminal (by pressing ctl+alt+F1) at any point during the boot process.

---

### Post by seted on 2008-04-28
I have installed the lastest drivers with EnvyNG. Same problem.

I have these two errors:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

(WW) ****INVALID MEM ALLOCATION**** b: 0xce000000 e: 0xce000000 correcting

---

### Post by Valpatine on 2008-04-29
I tried to install drivers straight from nvidia but it kept requesting Libc Development packages, which I downloaded and installed yet it still gave me the same error when installing. Should I have restarted after installing the Libc because it didn't tell me to, and none of the install guides mentioning having to restart.

---

### Post by Valpatine on 2008-05-04
Its been a week, is there anyone that can help me please? If I can't this to work I think I will just try PCLinuxOS 2008 but I would much rather have Ubuntu!

---

