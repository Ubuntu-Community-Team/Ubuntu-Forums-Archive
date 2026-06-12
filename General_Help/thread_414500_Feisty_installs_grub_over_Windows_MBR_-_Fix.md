---
title: "Feisty installs grub over Windows MBR - Fix"
date: 2007-04-19
forum: General Help
---

### Post by pumbers on 2007-04-19
I installed Edgy (6.10) a while ago on an external USB 2.0 hard drive without any problems - grub goes on the USB drive so to boot back to Win XP all I have to do is unplug the drive. However, when I installed Feisty (7.04) it came with an added shock: no option on where to install grub and my Win XP MBR got clobbered without being asked. Grub gives an error 21 on boot.

**Guys, come on - that's an M$ tactic!**

Anyway, once the panic was over I worked out this fix if you want to leave Feisty on your external drive when it's plugged in but still boot Win XP by default from your main drive:

First, assuming that you've installed Feisty on your external drive and are sitting there with an error 21 on screen, we need to restore the Windows MBR.

Boot from your Windows installation CD and select "R" to start the recovery console. Log on to your old Windows partition (probably c:/windows). Type the command "fixmbr" - it'll look like nothing has happened because the command only writes about 400 or so bytes to the disk, but it should have restored your Windows boot. Restart the machine to find out.

Second, let's get Feisty working again.

Everything Feisty needs to boot is still installed on the USB drive, all that's missing is grub from the MBR - but we can fix that. Boot from the Feisty Live CD, start a terminal session and type the command "grub". Now, we need to find which device to put grub on - type "find /boot/grub/stage1". Unless you've got ubuntu installed on several hard drives, you should get a response something like "(hd0,0)". 

Now to install grub to the MBR: type "root (hd0,0)", followed by "setup (hd0)". That should do it. You should now be able to boot from your external USB drive.

One last problem may still exist though. If grub still fails to boot, it may because it's trying to boot hd1 and not hd0. Short term, select the ubuntu boot image in the grub menu, type "e" to edit it. On the next screen, type "e" again to edit the entry and change "hd1" to "hd0", then press enter to save. Type "b" to boot that image and Feisty should start up.

Long term, edit the /boot/grub/medu.lst file and change entries reading "hd1,0" to "hd0,0". Fesity should boot normally next time.

---

### Post by LMelior on 2007-04-21
For the record, it does give you the option, but you have to click on the "Advanced..." button on the very last step.

Thanks for the rest though!

---

### Post by snl on 2007-04-24
> **LMelior said:**
> For the record, it does give you the option, but you have to click on the "Advanced..." button on the very last step.

Thanks for the rest though!

Where is the "Advanced..." button? Will it let you select where to install grub?

Thanks.

---

### Post by Rob Wesley on 2007-04-24
Perfect!  This is just the answer I was looking for.  Thanks a bunch.

---

### Post by LMelior on 2007-04-29
> **snl said:**
> Where is the "Advanced..." button? Will it let you select where to install grub?

Thanks.

If I recall correctly it's on the bottom right of the window, and actually I think the only purpose for it is to allow you to choose where to install grub.

---

### Post by TuxBobble on 2007-05-01
I was under the impression that I did things right.  I even looked in menu.lst, and all the instances of (hdn) are (hd0,0)...but it still freezes up.  It stops immediately when the Ubuntu logo appears, and the orange bar doesn't even start moving, In addition, I can't boot Windows XP (although the option is there...) because every time I try booting to XP, it just recycles the GRUB menu.

Does anyone know why this would occur?

---

