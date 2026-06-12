---
title: "[SOLVED] NVIDIA Driver Install ... still boots to X safe mode"
date: 2007-12-03
forum: General Help
---

### Post by matthewcraig on 2007-12-03
Greetings - have had NVIDIA working with the Ubuntu-supplied driver for a long while, but I wanted to try the NVIDIA-supplied driver as a temporary work-around for a bug.

I downloaded the NVIDIA-supplied driver from the NVIDIA website, compiled the binary into the kernel, and "vola!" everything worked.  Then, the next day, I turned on my computer and Ubuntu boots to Safe Mode.

**The only way I can go into X, after a reboot, without triggering Safe Mode, is re-installing the NVIDIA-supplied driver!**

Things I have tried that did not work:
Stopping the "gdm" process completely
Copying the old xorg.conf into /etc/X11 and restarting X
Running "nvidia-xconfig"

I suspect others run the NVIDIA-supplied driver out there.  Anyone see this sort of problem before?

---

### Post by NT4usB on 2007-12-03
Not since I used [Envy.]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by matthewcraig on 2007-12-03
I hear Envy can really screw up your dependency lists.  But, anyway, I looked over your link and I think I did everything listed there.  I just don't know what is happening to cause Ubuntu to fail back to Safe Mode on a reboot.  Is it maybe detection?  Where is the log file that I can monitor when this happens?  Will it be in the standard X log?

---

### Post by NT4usB on 2007-12-03
I've seen many problems posted wrt Envy but a hundred times as many success stories.
If your install is radically customized or mis configured in some way (like one of my boxes was*) Envy could break. 
I've had best results using Envy if I first select the uninstall option to completely remove the existing nvidia stuff. Then proceed direct to the install.
I think this is where most problems arise with Envy. Folks try every different way to get their video going and their box gets all conflicted. Then they run Envy and it can't make sense of the confusion and breaks.

I would think your Xorg.log would give a clue why it's failing now. Almost sounds like a permissions thing...

You try?```
sudo dpkg-reconfigure -phigh xserver-xorg
```

*(I had the latest kernel installed but grub wasn't booting to it. Envy configured for it but x failed when it booted the old kernel)

---

### Post by oscarsfriend on 2007-12-03
Matthew, I don't know about Gutsy as I am still on Feisty, but initially I could not get the nvidia drivers (the ones from nvidia not out of the repos) to work properly.  X would hang rather than start up in safe mode, however.  The solution I found was to add the following line to /etc/default/linux-restricted-modules-common:

> 
DISABLED_MODULES="nv nvidiafb nvidia_new nvidia_legacy"


The list of disabled drivers I got from running 'modprobe -l | grep "nvidia" -- note any match that doesn't end nvidia.ko and add to this list (removing the .ko and leading path).  After that it worked fine.

I figured this out when I found lines something like the following in /var/log/Xorg.0.log:

> 
Error: API mismatch: the NVIDIA kernel module has the version [some number], but
this X module has the version [some other number]. Please make sure that the kernel module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0): that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0): that the NVIDIA device files have been created properly.
(EE) NVIDIA(0): Please consult the NVIDIA README for details.
(EE) NVIDIA(0): *** ABORTING ***
(EE) Screen(s) found, but none have a usable configuration.


I don't know if this will solve your problem, but it might just work.

---

### Post by matthewcraig on 2007-12-04
Thank you all for taking the time and posting these helpful replies.


@oscarsfriend:
Quote: The solution I found was to add the following line to /etc/default/linux-restricted-modules-common:  DISABLED_MODULES="nv nvidiafb nvidia_new nvidia_legacy" 


Oh, snap!  I was so happily surprised to see X come up correctly after a reboot. THANK YOU!

---

### Post by Redmumba on 2007-12-09
I'd like to add to this, because I am having a similar problem but the above did not work.  I even tried adding it to the blacklist, and it STILL loads nvidiafb.  I am pulling my hair out on this one!  Why is nvidiafb being loaded even though it is blacklisted, disabled, etc.?  And I can't rmmod it because its always in use... argh!

(EDIT: Yes, it is built as a module)

---

### Post by Tails9 on 2008-02-20
> **Redmumba said:**
> I'd like to add to this, because I am having a similar problem but the above did not work.  I even tried adding it to the blacklist, and it STILL loads nvidiafb.  I am pulling my hair out on this one!  Why is nvidiafb being loaded even though it is blacklisted, disabled, etc.?  And I can't rmmod it because its always in use... argh!

(EDIT: Yes, it is built as a module)

Did you come up with a solution for this? The annoyance that nvidiafb is built in?

---

