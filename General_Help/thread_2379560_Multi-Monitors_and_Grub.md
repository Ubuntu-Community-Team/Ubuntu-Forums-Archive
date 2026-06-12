---
title: "Multi-Monitors and Grub"
date: 2017-12-06
forum: General Help
---

### Post by kilgor3 on 2017-12-06
Hello.

I have 3 monitors.  Two in landscape and one in portrait.  Of coarse the portrait one has to be my default monitor for my GFX card.  Everytime I boot up the grub selection menu is sideways.  Is there an easy way to setup grub to work in portrait mode?  Also, is there a way to set up the splash on my portrait monitor to not be sideways as well?

Thank you for your help!  :)

---

### Post by DuckHook on 2017-12-07
I know of no way to do what you are asking. I used to run four identical monitors in portrait mode. Since I often dropped into a shell session, your problem was especially acute in my case, since I had *no* monitor in landscape mode. I solved it with the following kernel setting:```
GRUB_CMDLINE_LINUX="fbcon=rotate:3"
```
Starting halfway through 12.04, Ubuntu compiled framebuffer rotation into the kernel. Therefore, this GRUB setting will rotate a shell session to display in portrait mode. It will not effect any GUI session, so you will still have whatever rotation you want for your desktop.

The problem is that GRUB loads before the kernel does. Therefore, kernel settings cannot effect GRUB, and GRUB itself is too primitive to do anything sophisticated with the framebuffer of your video card. In other words, you are stuck with an unrotated GRUB (although the above setting will cause your later boot processes to display properly in portrait orientation).

To be honest, I didn't find a right-angle GRUB or splash much of a problem, since I mainly used the default boot partition anyways. In your case, the above kernel parameter may not be desirable since you have two monitors in landscape.

---

### Post by kilgor3 on 2017-12-07
Thanks for the help.  I will mess with this on the weekend.  I may need to look into alternate bootloaders since I switch across three OS's multiple times through out the day.

---

### Post by DuckHook on 2017-12-07
> **kilgor3 said:**
> …I switch across three OS's multiple times through out the day.Have you considered the alternative of running them in VMs? Changing bootloaders is fraught with dangers and OS breakage.

---

