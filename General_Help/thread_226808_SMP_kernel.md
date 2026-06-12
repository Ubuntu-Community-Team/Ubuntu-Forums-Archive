---
title: "SMP kernel"
date: 2006-07-31
forum: General Help
---

### Post by canadianwriterman on 2006-07-31
I've been trying to upgrade the default 386 kernel to possibly work better on my P4 machine, particularly to take advantage of the Hyperthreading. It's a single core, but with HT (which is enabled in the BIOS).

I installed kernel-image-2.4.27-2-686-smp through Synaptic. When I reboot and select the SMP kernel, I get:

```
Kernel panic: VFS unable to mount root fs on 08:03
```

When I downloaded the standard 686 image and headers, it works fine, but I don't think hyperthreading will be available with it.

I also noticed in Synaptic that there are 686 pcmcia modules, but am not sure if I need them I am not running a laptop). Any help would be appreciated.

---

### Post by Ocxic on 2006-07-31
what filesystem are you using?? 
you can remove the pcmcia utils safly if you don't have a pcmcia card.

I would suggest completly remove the 686 kernel, reboot, and reinstall the kernel, sometimes it's just a glitch.

---

### Post by testube_babies on 2006-07-31
I think the normal 686 kernel should be fine.  Try ```
cat /proc/cpuinfo
```

If it shows processor:0 and processor:1 then your hyperthreading is enabled.  If it only shows processor:0 then you need to try installing the SMP kernel again.

---

### Post by canadianwriterman on 2006-07-31
It shows only 1 processor. Do I need to enable hyperthreading in GRUB? I read somewhere that I need to add ht=on, but I'm not sure where in GRUB it needs to be added.

---

### Post by canadianwriterman on 2006-07-31
I'm using the standard file system installed (ext3... I forget). Removal and reinstallation does not work. For some ready, my BIOS does not like the SMP kernel, but does load the regular 686 kernel. I wanted the 686 kernel to reduce the load on my CPU. It was hitting 100% with the 386 kernel, but maxed at about 20% with the 686 kernel.

The pronlem I have with the standard 686 kernel is that my system freezes randomly and cannot be unlocked. Only rebooting releases it.

---

### Post by blitzd on 2006-07-31
Could be that the SMP kernel doesn't have the driver for your SATA controller or the filesystem you are using built in. Do you know what driver you need for the controller or filesystem?

---

### Post by canadianwriterman on 2006-07-31
Uncertain about the drivers for the 686-SMP. However, I have another question. I've installed the linux-image-2.6.15-26-686 and also linux-image-686 (not sure if I needed to). I see ther are also kernel-image files for 686. What's the difference between linux-image and kernel-image files?

---

### Post by canadianwriterman on 2006-07-31
Moving this to a new thread.

---

### Post by blitzd on 2006-07-31
> **canadianwriterman said:**
> Uncertain about the drivers for the 686-SMP. However, I have another question. I've installed the linux-image-2.6.15-26-686 and also linux-image-686 (not sure if I needed to). I see ther are also kernel-image files for 686. What's the difference between linux-image and kernel-image files?

The kernel-image packages are for old 2.4 kernels, linux-image are for 2.6.

I installed linux-686-smp (kind of a virtual package consisting mainly of dependencies for the other SMP packages you need) and it was the only package I needed.

---

### Post by canadianwriterman on 2006-07-31
Thanks,blitzd. I did install the SMP kernel, but my BIOS dows't like it. I installed the regular 686 kernel and now I have some boost in speed and a huge decrese in CPU usage. I guess I can do without the hyperthreading.

---

