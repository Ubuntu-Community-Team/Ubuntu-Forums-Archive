---
title: "Ubuntu edgy boot seems slow"
date: 2006-11-02
forum: General Help
---

### Post by noxxle on 2006-11-02
It takes about 60 seconds from when i push the power on button on my laptop until I can reach my desktop, is that normal? I seem to recall dapper taking about 45s. I have automatic login too, the 60s counts the gui login and gnome loading up. Still seems long. Using a pentium M 1.8 dual core with 1gig of ram. How long does it take you to boot to desktop?

---

### Post by noxxle on 2006-11-02
meow

---

### Post by lassegs on 2006-11-03
I have the exact same problem. For me i think this is easy fixable, if only i could get out of the bootup-image, and see whats going on, but when i press ESC or alt-ctrl-F1 the image just freezes and continues to boot. How can I disable bootup-image?

---

### Post by narfg on 2006-11-03
To remove the splash screen you just have to remove the "splash" option in your "/boot/grub/menu.lst". Optionally you can remove the "quiet" option to really see what's going on :)
Btw, edgy takes about 1 minute to boot on my notebook. Dapper only took around 30 seconds.

---

### Post by McGregor927 on 2006-11-03
Kubuntu has the same problems.  I installed 6.06 and then painfully upgraded to 6.10 and it would run just fine.  But if I install from the CD it boots terribly slow and everything seems to run really sluggish. I posted the boot chart on another thread but haven't got any responses on why things are taking so long. My boot time on dapper were around 35 - 40 seconds.  Now from  a fresh edgy install around 90 seconds.

---

### Post by TSJason on 2006-11-22
Hi,

 I had this problem on a workstation too. I removed the linux-restricted-modules package and it seemed fix it right up. I am running the nvidia beta drivers so I don't really need it anyway. 

*Note - be sure you don't remove the lrm-common package if you try this. You'll still need those scripts to get X going, with the nvidia beta anyway.

---

