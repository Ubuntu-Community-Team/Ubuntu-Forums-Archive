---
title: "Help with Nvidia."
date: 2007-09-07
forum: General Help
---

### Post by nymusicman on 2007-09-07
I have a Nvidia MX 4000 video card. The driver I have to use is Latest Legacy GPU version (1.0-96xx series): 1.0-9639. Because this legacy driver is not in the repositories, I have to use the binary off Nvidia's website. Not really a problem. The problem is that I also have a few games installed on my Linux box which requires having mesa libraries. Nvidia's driver and mesa library have a conflict with the opengl files. Also not really a problem when my computer is running, I just install Nvidia's drivers after mesa and everything is overwritten and it works.

The real problem I'm having is that whenever I reboot the computer X won't start until I reinstall Nvidia's drivers. Now because X won't start I still really don't have a problem with this being the Nvidia's drivers require X to be closed. It is an annoyance but i really don't turn my computer off that much. But now I'm hearing that Gutsy will have an X safemode, so now I'm realizing I need to take care of this problem once and for all. Please help.

---

### Post by pointone on 2007-09-07
When X doesn't start, what error messages are displayed? (Check /var/log, too!)

---

### Post by nymusicman on 2007-09-08
Okay here is the deal. I got as far as finding out that my nvidia driver is not being loaded in the kernel when I restart my computer. So here is what I did.

Before I loaded the Nvidia driver I typed:
> # lsmod | sort > /tmp/nvidia-before
And After I typed:
> # lsmod | sort > /tmp/nvidia-after
# diff /tmp/vidia-before /tmp/nvidia-after

And here was the output.
>   7c7
< agpgart 35788 2 nvidia,via_agp
---
> agpgart 35788 1 via_agp
57d56
< nvidia 3930860 0

My question was what do I do from here? I'm not quite sure where to find the modules the kernel loads.

---

### Post by fragos on 2007-09-08
In the Ubuntu repositories is the package "nvidia-glx" which is 1.0.9631 which should work with the MX4000.  The three different glx packages are suppossed to cover all but perhaps some 8000 series cards.

---

