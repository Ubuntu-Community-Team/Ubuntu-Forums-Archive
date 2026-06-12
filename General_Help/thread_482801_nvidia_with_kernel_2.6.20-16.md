---
title: "nvidia with kernel 2.6.20-16"
date: 2007-06-24
forum: General Help
---

### Post by akudewan on 2007-06-24
When I use the latest kernel: 2.6.20-16, nvidia doesn't work, and I get an error saying "No screens found". I have installed the package: linux-restricted-modules-2.6.20-16-generic, that claims to have the nvidia module.

I read on some thread that some people needed to install the nvidia-glx-new package. I have a Geforce4 MX 440, and the description of this package says:
> 
If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy package instead of this one. If you have a GeForce4, you may need the nvidia-glx package.


I already have nvidia-glx, and I even tried "nvidia-glx-config enable" when I booted from the new kernel.

Manually installing the driver would be the last option for me. Does anyone have any ideas on how I can fix this?

---

### Post by meech on 2007-06-24
I am also battling with this issue and am still discovering what exactly I have to have to make this work. Upgrading to Feisty and reinstalling NVIDIA has been more difficult than reinstalling it in the past.

---

### Post by akudewan on 2007-06-29
There were some "restricted packages" updates today, along with nvidia-glx. Installing these has fixed the problem. :)

---

### Post by Pheodax on 2007-06-29
> **akudewan said:**
> There were some "restricted packages" updates today, along with nvidia-glx. Installing these has fixed the problem. :)
That's funny. The new updates caused my drivers to brake today, actually. I had used Envy to update to the latest ("bleeding edge") drivers. It compiles a modified NVIDIA kernel using the Linux kernel source (correct me if I'm wrong, I have been using Linux for 2 weeks now). I completely removed the NVIDIA drivers using Envy and then reinstalled them using Envy as well. This fixed the problem :) Now I'm back on 100.11.14

---

### Post by fragos on 2007-06-29
> **Pheodax said:**
> That's funny. The new updates caused my drivers to brake today, actually. I had used Envy to update to the latest ("bleeding edge") drivers. It compiles a modified NVIDIA kernel using the Linux kernel source (correct me if I'm wrong, I have been using Linux for 2 weeks now). I completely removed the NVIDIA drivers using Envy and then reinstalled them using Envy as well. This fixed the problem :) Now I'm back on 100.11.14

If you don't use the Ubuntu repositories to install nvidia drivers there's a good chance that kernel updates will break your system.  The best choice from a stability perspective seems to be the appropriate nvidia-glx package.  When kernels update, drivers need to be recompiled.  With nvidia-glx packages, Ubuntu does this for you when they update the kernel.

---

### Post by justtech on 2007-06-29
so now that mine are broken... how do I go about fixing it from the command promt since I can't get back into the X server

---

### Post by fragos on 2007-06-29
There's more than one way to handle this but I'd do the following:

sudo nano ect/X11/xorg.conf

Find where the following section.  Yours may differ from this one.

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

change "nvidia" to "nv" and save the file.

When you reboot you shoild have X with the open source driver.  Now I use synaptic to install the appropriate nvidia-glx package.  This should get you in sync with the Ubuntu repositories.  You may need to edit /etc/X11/xorg.conf again to say "nvidia".

---

### Post by justtech on 2007-06-29
awesome... ty

---

