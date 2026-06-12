---
title: "periodic X crashes w/intel 945gm"
date: 2008-06-17
forum: General Help
---

### Post by zeus77 on 2008-06-17
Hi.  This computer uses the Intel 945GM graphics chipset.  It ran fine under Edgy, Feisty, and Gutsy.  After the upgrade to Hardy, however, X periodically crashes when I try to view a video (mpg and/or DVD), though the behavior seems a bit random.  In my syslog, strangely, I get errors about nvidia.  But I don't have an nvidia card.  Here is an example:
```
Jun 17 00:29:13 loglady modprobe: WARNING: Error running install command for nvidia 
Jun 17 00:29:21 loglady gdm[21340]: WARNING: gdm_slave_xioerror_handler: Fatal X 
  error - Restarting :0
```

For the heck of it, I deleted the file /etc/modprobe.d/nvidia-kernel-nkc.  Then, the errors changed to:
```
Jun 17 10:36:13 loglady kernel: [ 1327.762837] nvidia: module license 'NVIDIA' taints
  kernel.
Jun 17 10:36:13 loglady kernel: [ 1405.644568] NVRM: No NVIDIA graphics adapter found!
Jun 17 10:36:13 loglady modprobe: FATAL: Error inserting nvidia
  (/lib/modules/2.6.24-19-generic/volatile/nvidia.ko): No such device 
Jun 17 10:36:43 loglady gdm[5984]: WARNING: gdm_slave_xioerror_handler: Fatal X
  error - Restarting :0 
```

The relevant portion of xorg.conf looks like this:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I remember hearing that xorg.conf behavior got changed in Hardy -- and indeed I see no mention of the intel driver there.  On the other hand, it seems that the intel driver is working fine since it is able to run Compiz, etc (though I always have it disabled, and the above described behavior holds true when Compiz is disabled).  Where do graphics parameters get set now if not in xorg.conf?

And most importantly: any ideas why Hardy is trying to install the nvidia module whenever I watch a video?  

Thanks!
zeus77

---

### Post by Tom--d on 2008-06-17
Weird :\

I have the same graphics card. same xorg.conf and experience no errors at all (far as i know off tho)

Search for nvidia kernel in sypatic and see what comes up. See if anything is related etc.

---

### Post by zeus77 on 2008-06-17
The package nvidia-kernel-common is installed, but I think this is installed for everyone.  If I try to uninstall it, it wants to uninstall the linux restricted modules, which is presumably a dependency.

Note that nvidia-glx **is not** installed, while xserver-xorg-video-intel **is** installed.

zeus77

---

