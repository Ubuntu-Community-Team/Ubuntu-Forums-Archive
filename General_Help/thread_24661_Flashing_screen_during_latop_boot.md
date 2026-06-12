---
title: "Flashing screen during latop boot"
date: 2005-04-07
forum: General Help
---

### Post by cell-gfx on 2005-04-07
Whenever I boot the LiveCD on my NEC laptop, the screen flickers on and off. This happens so much that the any of the text-based boot information is nearly unreadable. Once Unbuntu gets into Gnome, everything is fine and the resolution sorts itself out. 

My laptop is running an ATI Radeon 9100 IGP Mobile graphics chip.

Can anyone help?

---

### Post by kiddo on 2005-04-08
Just a quick thought, could this be live-cd related? I mean, maybe it could work flawlessly if it was installed to the HDD

---

### Post by cell-gfx on 2005-04-10
[QUOTE=kiddo]Just a quick thought, could this be live-cd related? I mean, maybe it could work flawlessly if it was installed to the HDD[/QUOTE]

Well, _maybe_ but as the whole purpose of running a LiveCD is to not have to install to the HD, I think that's quite an extreme solution. Plus, the flickering happens during the LiveCD bootup, so unless the actual install CD boot process is coded completely differently, I would expect the same problem.

It seems like my laptop can't handle the default resolution and refresh rate that the LiveCD uses. Can anyone tell me what that is currently set to, so I can check to see if this is the problem?

Cheers.

---

### Post by la-karaviro on 2005-04-13
i have a similar problem here, on the boot, after hotplug, the screen starts to run from right to left and is squized to the bottom, so unreadable, but as soon the gdm is startet everything is fine again

i use Ubuntu Horay Hedgehog 5.04 on a PC x86, and i have an ATI graphic card,

i wanted to install the new driver from ATI but after i quit the GDM, dont know if this is nececcery im a newbie, the screen starts again flickering and i cant see anything to do the commands.

would be happy about help, hope i said all needed information?

---

### Post by Fujiyama on 2005-05-09
I'm to having the same problem, booting from the installmedium the screen is flickering sick.. Im running on a ASUS A4000K, Radeon 9700 Mobility.. Not a nice start for Ubuntu in my eyes 8-/

---

### Post by Misan on 2005-08-03
Hi!

I have the same problem with flickering screen on ASUS M6738RB laptop. There is ATI Mobility Radeon 9100 IGP.
I have tried Live Ubuntu 5.04, Live Kubuntu 5.04, Install CD Ubuntu 5.04, Install CD Kubuntu 5.04 and it was always the same problem.

I have tried to boot Live CD with few parameters and only working was:

```
live vga=771 acpi=off
```  for Live CD. 

I don't know what param to type when you want to run installation disc. I think it will be similar. Probably without 'live'. Check for help ( F5, F6 or so)

Good Luck! 

Sorry for my english...   :roll:

---

