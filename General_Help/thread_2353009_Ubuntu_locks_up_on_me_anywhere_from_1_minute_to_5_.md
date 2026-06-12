---
title: "Ubuntu locks up on me anywhere from 1 minute to 5 minutes after boot"
date: 2017-02-17
forum: General Help
---

### Post by coldstreak18 on 2017-02-17
I installed Elementary OS and had an issue where it would lock up after about 5 minutes The whole machine was useless, I had to hard reboot after a lot of fiddling I gave up and installed Ubuntu 16.04.2 thinking it was an issue with eOS. I am having the same exact issue. I updated the kernel to 4.9 I updated a line in grub to 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1" 
```

I made sure all updates were installed. I haven't updated my Nvidia drivers this time but I have in the past and that never worked.

I don't know what else to do, what could be causing my machine to lock up?

I dual boot Win10 and that works flawlessly.

Hardware
CPU: Intel i5 4690K
GPU: Nvidia GTX 660
MB: ASRock Z97 Pro4
Ram: 12 GB
HDDs: 
Ubuntu installed on 120GB SSD
Windows on 500GB SSD
3 TB Platter drive

---

### Post by mörgæs on 2017-02-18
Have you tried running memtest from the boot menu?

---

### Post by RobGoss on 2017-02-18
>  I made sure all updates were installed. I haven't updated my Nvidia drivers this time but I have in the past and that never worked.    


Have you tried installing the proprietary drivers provided by Ubuntu? it's worth a shot

---

### Post by joegp on 2017-02-18
i think i have a similar problem to yours, but mine doesn't lock up, at least not completely (tours might not either), it snaps out of it after a few minutes, but if i try and do something, specially multiple things at once, it locks up again (for a few minutes).
This is on 16.04.2 with all the updates and proprietary drivers, same thing with default drives.
It was even worse on 16.04.1 and 16.10 (and KDE Neon, and Ubuntu Mate, basically anything ubuntu based)
And even worse than that while my bios was in Legacy mode (now it's in UEFI)

My questions would be:
Do other distros work fine ? what about non ubuntu based ?
what mode is your bios in ? (legacy or UEFI)

Try reinstalling ubuntu with only a single drive in use, try it on a different drive. (if you can)

---

