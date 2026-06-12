---
title: "Update rollback?"
date: 2007-04-12
forum: General Help
---

### Post by QwUo173Hy on 2007-04-12
Is it possible to 'undo' an update? There's an update pending with kernel updates and in the past this has left me and my neighbour with machines that won't boot. My system is fine at the moment so I might just leave it be if I can't roll back the update.

Thanks for reading,
Jarlath

---

### Post by MoLE on 2007-04-20
This has definitely happened to me previously, particularly with proprietary kernel modules, such as nvidia drivers and vmware kernel modules.

Certainly with new kernels, the update manager will not automatically remove your old kernel.  So if you have any problems, then you can easily boot into the old kernel via the Grub menu, until you are certain everything works under the newer kernel.

HTH.

---

### Post by QwUo173Hy on 2007-04-22
Thanks MoLE. I'll keep that in mind. I never really watch the boot process and forgot that I can intervene at boot time.

Jarlath

---

### Post by Genius695 on 2007-05-28
I've recently (this morning) allowed updates to go through, there were some kernel ones and a vmware one. When I rebooted, I could no longer mount my secondary internal harddrives (vie the mounter applet), I was also inable to do it in Terminal.

I rely on these drives a lot, and they have most of my stuff on them. Any help would be appreciated.


Thanx in advance,
Spencer K.

---

### Post by QwUo173Hy on 2007-05-28
Genius - did you try selecting the previous kernel at boot time? As MoLE mentioned in his post, this is now possible.

---

### Post by mlentink on 2007-05-29
> **jarlath said:**
> Genius - did you try selecting the previous kernel at boot time? As MoLE mentioned in his post, this is now possible.

How does one do this? 
After the latest kernel update my Sweex (Atheros) WiFi Card is no longer recognized, so I'd appreciate a pojnter in the right direction

---

### Post by Limitlesschannels on 2007-05-29
i believe jarlath was referring to the grub screen where (assuming you are dual booting) it has the other OSs to load listed.  Then you just arrow down to the older kernel; i.e. lower number, heh, and you are good.

---

### Post by mlentink on 2007-05-29
Thanks.
But I don't have a dual-boot system, mine is Ubuntu only. Does that mean it won't be possible to boot into an earlier kernel?

---

### Post by QwUo173Hy on 2007-05-29
You don't have to be dual boot for this. I have only Ubuntu myself. GRUB gets installed regardless.

When you turn on your computer, the BIOS does it's thing and then GRUB does a countdown (visible on screen) from 3 down to 0. You have to press ESC (I think) here to get the list of kernels.

---

### Post by Bigdog60 on 2007-05-29
Yeah at boot time remove the kernal

---

### Post by mlentink on 2007-05-29
Thanks Jarlath!

I'll try that as soon as I'm back home.

---

### Post by mlentink on 2007-05-29
I did what Jarlath advised me to do and it works. Pressing [Esc] while booting brings up the menu.

I'm now back in the previous kernel and tada.... my Atheros card works again.

So the problem is directly related to the new kernel. I'll have a look to see whether this had been reported as a bug on Launchpad.

Thx again Jarlath!

---

### Post by QwUo173Hy on 2007-05-29
You're very welcome mlentink :)

---

