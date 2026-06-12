---
title: "Changed video card from ATI to nVidia and can't boot"
date: 2008-04-15
forum: General Help
---

### Post by CosmicSlop on 2008-04-15
Help!!!

I switched my video card from an ATI to and nVidia 6000 series and now... when I boot to 7.10 my screen is BLANK. During the boot process I get the splash screen then first arrow but never the login screen. 

I'm running a duel monitor setup with one DVI (screen1)  and one analog monitor(screen2). Neither give me a picture. The analog screen does, however, have a faint greyscale flicker.

Any help would be appreciated.

Thanks.

---

### Post by lswest on 2008-04-15
Did you change the driver before you replaced the cards?  If not, when you get to the blank screen, hit ctrl+alt+F1 and log in to the terminal then type```
sudo dpkg-reconfigure -phigh xserver-xorg
``` it should give you your GUI back, however, you will need to probably install the Nvidia drivers manually.

---

### Post by CosmicSlop on 2008-04-15
No I wasn't smart enough to remember to change the drivers in Ubuntu first. I'll give your suggestion a try.

Thanks

---

### Post by CosmicSlop on 2008-04-15
> **lswest said:**
> Did you change the driver before you replaced the cards?  If not, when you get to the blank screen, hit ctrl+alt+F1 and log in to the terminal then type```
sudo dpkg-reconfigure -phigh xserver-xorg
``` it should give you your GUI back, however, you will need to probably install the Nvidia drivers manually.

This did not work. Pressing ctrl+alt+F1 did nothing. Nothing changed, the screen was still blank.

---

### Post by lswest on 2008-04-16
sorry about not replying sooner, been busy.  Can you boot into recovery mode then? (when GRUB is loading hit "esc" to get into the menu, and choose the second line, should be the recovery mode) and it'll drop you into a root prompt, then give in the command i posted above, minus the sudo.

---

### Post by methodical on 2008-04-27
> **lswest said:**
> sorry about not replying sooner, been busy.  Can you boot into recovery mode then? (when GRUB is loading hit "esc" to get into the menu, and choose the second line, should be the recovery mode) and it'll drop you into a root prompt, then give in the command i posted above, minus the sudo.

I am having this same problem. I switched video cards from ATI to nVidia, and Ubuntu freezes on the loading screen. I tried to boot into recovery mode, but the computer hangs when it gets to "Configuring network interfaces...". What is going on here? I have not altered any network settings.

---

### Post by methodical on 2008-04-27
> **methodical said:**
> I am having this same problem. I switched video cards from ATI to nVidia, and Ubuntu freezes on the loading screen. I tried to boot into recovery mode, but the computer hangs when it gets to "Configuring network interfaces...". What is going on here? I have not altered any network settings.

Ok nevermind. I got it to work. I was able to Ctrl+C right before it go to that.

---

