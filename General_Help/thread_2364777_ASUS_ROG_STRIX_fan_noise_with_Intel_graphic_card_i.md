---
title: "ASUS ROG STRIX fan noise with Intel graphic card in Ubuntu 16.04"
date: 2017-06-27
forum: General Help
---

### Post by MsKK on 2017-06-27
Hello Everyone!

I have an ASUS ROG STRIX GL753VD and I just installed Ubuntu 16.04 on it. It has a hybrid configuration of graphic cards with an integrated Intel HD Graphics 630 and a dedicated NVIDIA GeForce GTX 1050. I installed nvidia-381 and the switching works well. To avoid some known issues, I added

```
acpi_osi=Linux idle=nomwait nouveau.modeset=0 acpi_backlight=native
```

at the grub configuration file in GRUB_CMDLINE_LINUX_DEFAULT="quiet splash". I don't use "acpi_osi=" nor "acpi_osi=!" because they disable the touchpad. And I already tried setting "acpi_osi=vendor" with no results. Also, the "acpi_backlight=native" option doesn't seem to do anything. 

The problem is that whenever I switch to the Intel graphic card, the fan starts going at 100% (making a lot of noise but no high temperature) and Ubuntu gets stuck on shutdown (these things DON'T happen when I use the NVIDIA card). I am using NVIDIA X Server to switch. My kernel is 4.8.0-56-generic. 

Additional problems are that the FN backlight and brightness buttons don't work (F1 to F9). The volume (F10 to F12) DOES work though.

If anyone has similar issues and has solved them, I would gladly appreciate it.  

 
[FONT=Verdana]
[/FONT]

---

