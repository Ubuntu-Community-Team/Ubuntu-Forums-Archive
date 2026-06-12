---
title: "Ubuntu 18.04 hangs on reboot/shutdown (Asus ROG Zephyrus G GU502)"
date: 2020-06-05
forum: General Help
---

### Post by jchwenger on 2020-06-05
[B]Edit: the issue seems to stem from libvirtd and libvirt-guests daemons, and possibly also the fwupd. Making sure none of them are running before reboot solves the issue.

To do:
- find proper way of configuring libvirt/qemu so that this doesn't happen;
- disable certain updates (nvidia-related) as only specific versions work with Tensorflow, and it might be that fwupd stays up because those unwanted updates are detected.[/B]

***

Hi,

I'm having this issue where I can no longer reboot or shutdown without the laptop hanging indefinitely. 

I had modified my grub file the following way:

```


# https://ubuntuforums.org/showthread.php?t=2420199
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.modeset=0 tpm_tis.interrupts=0 acpi_osi=Linux i915.preliminary_hw_support=1 idle=nomwait"
```

And for a while it worked just fine. I don't know what changed, if it's an update, a program I installed, I'm unable to remember. Now I am forced to press the power button 5 seconds to make it shutdown... I tried a few different options with that grub config, bringing back some old problems (e.g. display resolution screwed, stuck on boot, etc.). 

Does anyone know of a solution, or at least how to go about debugging this ?

Thanks very much in advance!

---

### Post by izznogooood on 2020-06-05
After you make changes do you run "update-grub" ? If not do it! :)

1. Remove all the modifications to grub and see if it fixes the problem
    1.2 If the problem still persists, take note of the time you shut down, then on reboot run "journalctl -r" and go down (back in time and see what makes your computer hang at shutdown.
    1.3 If other problem, change topic and address new problem :)
2. Try adding the modifications and apply them one by one to find the one which is making your system hang.
3. Try googling that change and hanging shutdown for a solution.

---

### Post by jchwenger on 2020-06-06
Hi, thanks a lot for this!

So, yes, update-grub all done.
1. Good point. Seems like the problem persists, revising my hypothesis. It might not come from the grub config at all, but maybe from something I installed.
1.2 Thanks for the tip, didn't know `journalctl`, such a jungle! I'll see if I can find something.
2-3. Standard procedure indeed, although in this case reading the journalctl will be the primary hurdle :D.

One question perhaps, if you have the time: is it safe to post (some) of the output of those logs here? Thanks again!

---

### Post by kema77 on 2020-06-07
I don't know if this is the case in your situation, but the "hanging" issue I experience with Ubuntu 18.04 reboots/shutdowns occurs when the firmware updater daemon (fwupd in system monitor) is running. Usually it is not a problem because the daemon goes into suspend mode after and hour or so of uptime. However, it awakens whenever I run the software updater, which is expected I would think. I now always check before rebooting and then kill it first if it is active.

---

### Post by jchwenger on 2020-06-08
Thanks for this @kema77, I tried, but to no avail, the hanging is still there. 

I hadn't update all the cuda paraphernalia either, since it breaks Tensorflow 2.1 with GPU (I tried updating, the system still hang, and the TF installation broke, so I reinstalled everything as I had before).

[I pasted a cut from the `journalctl -l` which may contain the required information... (Is it ok to post these things btw?)]("https://pastebin.com/mb84cQwN")

Thanks again for everyone's help, I'm definitely running in circles with this.

---

### Post by jchwenger on 2020-06-10
Ok, I think the culprit was primarily `libvirtd`, a virtual-machine-related daemon. So far my solution was to uninstall & disable everything related to kvm. Might also be `fwupd` as well, will have to do more testing.

---

### Post by dino99 on 2020-06-10
From 'journalctl -b' grab errors (red lines) and warnings (yellow ones) to let you know what you can dig about

---

### Post by jchwenger on 2020-06-10
Oh, thanks a lot @dino99, I did spend quite some time digging into journalctl, as posted [here]("https://pastebin.com/mb84cQwN") for instance, but it's as if the problem came after all that. In any case, I could solve it by uninstalling everything related to virtual machines (qemu, libvirt), and fully disabling/removing the libvirt-guests and libvirtd daemons. I still need to check whether I also need to kill fwupd, as @kema77 pointed out (which might still be up because I can't update a lot of Nvidia components to the latest version, as I need specific versions for my Tensorflow config to work).

---

