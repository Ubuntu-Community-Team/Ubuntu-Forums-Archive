---
title: "Upgrading MOBO and graphics card"
date: 2007-10-13
forum: General Help
---

### Post by GuiGuy on 2007-10-13
My Ubuntu box is playing up and I think it is time to upgrade the motherboard and graphics card.

On Windows the procedure is relatively easy - replace the hardware components, boot from the setup CD and do a repair. 

My experiences with linux have been quite different.  Usually I was left staring at a shell giving me meaningless cryptic error messages and command line prompt. Generally I'd have absolutely no idea what to do next, so I'd rebuild from scratch and retrieve workfiles from backups. Very time consuming.

Is there are better way?

Thanks

---

### Post by Anolis on 2007-10-13
> **GuiGuy said:**
> 
Is there are better way?


sounds like you just need to reinstall your graphics card drivers, what card did you install?

---

### Post by coffeecat on 2007-10-13
> **GuiGuy said:**
> On Windows the procedure is relatively easy - replace the hardware components, boot from the setup CD and do a repair.

And then have Windows throw a wobbly because the hardware is different and say it needs re-activating. And then having to convince some suspicious M$ lacky in a call-centre to give you a code to unlock the OS. :wink:

> **GuiGuy said:**
> My experiences with linux have been quite different. Usually I was left staring at a shell giving me meaningless cryptic error messages and command line prompt. Generally I'd have absolutely no idea what to do next

In almost all cases this sort of thing is caused by a change of graphics chipset. This, admittedly, is the weak point, but it's getting better as the x-server windowing system is being further developed. Actually, the Linux kernel is much more robust than the Windows one when confronted with different hardware, and it **doesn't require re-activation**. :) I once installed a minor distro (an early version of Foresight) on a 64-bit AMD system with VIA chipset (the OS was 32-bit admittedly), took out the HD, put it in an Intel chipset/Intel CPU machine and it booted up with great aplomb into the GUI. Not an error message in sight.

But to your particular problem. Apart from the graphics chipset, you'll only get a problem if you are unlucky enough to choose hardware that is not supported in the kernel. Suggest you search on this forum and google for your chosen m'board. With graphics, if you get the same card/chipset, you won't have a problem, and if you need to get something different, suggest you avoid ATI for now and go for Nvidia or Intel. If the GUI crashes on bootup, simply do

```
sudo dpkg-reconfigure -phigh xserver-xorg
``` from the shell and reboot.

---

### Post by GuiGuy on 2007-10-13
> **coffeecat said:**
> And then have Windows throw a wobbly because the hardware is different and say it needs re-activating. And then having to convince some suspicious M$ lacky in a call-centre to give you a code to unlock the OS. :wink:

No, not in my case :wink:

> 
In almost all cases this sort of thing is caused by a change of graphics chipset. 


Yea, that's where it's turned into disaster for me in the past.

> 
But to your particular problem. Apart from the graphics chipset, you'll only get a problem if you are unlucky enough to choose hardware that is not supported in the kernel. Suggest you search on this forum and google for your chosen m'board. With graphics, if you get the same card/chipset, you won't have a problem, and if you need to get something different, suggest you avoid ATI for now and go for Nvidia or Intel. If the GUI crashes on bootup, simply do
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` from the shell and reboot.

Thanks

---

### Post by GuiGuy on 2007-10-13
> **Anolis said:**
> sounds like you just need to reinstall your graphics card drivers, what card did you install?

I want to replace the MOBO and the graphics card. The current GFX is ATI AGP, the new one will probably be a mid-range nvidia PCIE.

---

### Post by coffeecat on 2007-10-14
> **GuiGuy said:**
> The current GFX is ATI AGP, the new one will probably be a mid-range nvidia PCIE.

Yes, that will cause an oops if you are using Feisty. But the command I suggested should sort it.

Things are getting better though. I believe that Gutsy has a GUI failsafe wotsit (sorry about the technical jargon :) ) such that it will boot into VESA mode in such a situation. VESA is pretty basic, but at least you still have a GUI and can then re-configure things in the GUI.

Actually, that failsafe Vesa fallback is better than what Windows sometimes does. I have an old-ish machine with onboard Intel 845G graphics which doesn't support anything better than 1280x1028 (in Windows or in Linux). I downloaded the latest Windows driver from the  Intel website and Windows promptly crashed such that I could only get a 640x480 desktop :roll:. I did a system restore and got my desktop back, and then bought a cheap-n-cheerful ATI Radeon 9250 PCI card. Yes - the machine doesn't have an AGP or PCIe slot. I remembered to install the ATI driver **before** installing the card, rebooted the machine with the card in place and Windows promptly crashed into 640x480 mode again. :(

It was quite difficult right-clicking between the monstrous icons that were completely covering the desktop in order to adjust the screen resolution but eventually I got the 1680x1050 resolution I wanted.

But you've got a point. Fedora has managed to cope with graphics card changes since version 3 at least. You got error messages on bootup, but you still booted into a GUI. So it has been possible in Linux with an earlier version of the xserver for quite some time. The fact that other distros have not been able to do the same is very bad - imo.

---

