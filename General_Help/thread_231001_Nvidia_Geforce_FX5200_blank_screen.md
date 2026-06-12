---
title: "Nvidia Geforce FX5200 blank screen"
date: 2006-08-06
forum: General Help
---

### Post by plb on 2006-08-06
Whats the deal with this card...is nvidia ever going to fix the drivers to a working state? Used to work fine some time ago, don't remember the exact driver I used. Are there any workarounds to fix this thing and what driver(s) is it that work with this again?

---

### Post by simonn on 2006-08-06
> **plb said:**
> Whats the deal with this card...is nvidia ever going to fix the drivers to a working state?

The current drivers work fine.

> Used to work fine some time ago, don't remember the exact driver I used.

They still work fine. Have done for the past few years.

> Are there any workarounds to fix this thing and what driver(s) is it that work with this again?

Yes, the drivers in the Ubuntu repositories work:

nvidia-glx
nvidia-kernel-common
linux-restricted-modules-[kernel version]

You may have to remove any nvidia driver files that exist on your system now (no, I do not know what the files are called or where they are located, but [https://help.ubuntu.com/community/NvidiaHoaryRemoval](https://help.ubuntu.com/community/NvidiaHoaryRemoval) may help).

---

### Post by plb on 2006-08-06
Don't work for me unless I disable agpcart which gives crappy performance.

---

### Post by orb9220 on 2006-08-07
using 5200 myself on dual screens works great 3d support and twinview.

You must not have the nvidia-glx drivers installed or your xorg.conf file configured right or both.

Just run nvidia-settings in a term if it is blank or if it is command not found then you don't have the nvidia drivers.

Post your xorg.conf file here for help.

---

### Post by simonn on 2006-08-07
What is returned when you do:

```

lsmod | grep agp

```

---

### Post by simonn on 2006-08-07
I had an indepth look at this last night and found it to be the sis_agp driver that was causing the problem.

```

$ cat /proc/driver/nvidia/agp/status

```

Should return something like:

```

Status: 	 Enabled
Driver: 	 AGPGART
AGP Rate: 	 8x
Fast Writes: 	 Disabled
SBA: 		 Enabled

```

If it does then all is well. Note, I do not going into depth about Fast Writes and SBA here, because my motherboard does not support Fast Writes. There is plenty on the net about enabling them - if your hardware support it.

If it returns 

```

Status: 	 Disabled

Blah blah blah...

```

Then all is not well.

Make a backup of /etc/X11/xorg.conf. No, really, make a backup. Do not rely on comments. I have had X actually overwrite xorg.conf with garbage before.

Set the following in the "Device" section of /etc/X11/xorg.conf

```

       Option        "NvAGP" "2"

```

This will force xorg to use agpgart. Which means that if agpgart is not working on your system then you will get the blank screen symptom you are experiencing.

```

lsmod | grep agp

```

Returns a list of the agp drivers installed, in my case it was originally

agpgart
sis_agp
amd64_agp

By blacklisting all possible combinations of the sis_agp and amd64_agp drivers I determined it was the agp_sis driver causing the problem.

To blacklist a driver add the following to the end of /etc/modprobe.d/blacklist:

```

blacklist [driver]

```

In my case:

```

blacklist sis_agp

```

Then reboot.

If you still get the blank screen, boot into safe mode and try blacklisting other agp drivers. If still no joy, then I guess you hardware combination does not suport agpgart - unlikely if it has before.

All is well when you can boot into X and cat /proc/driver/nvidia/agp/status returns something like:

```

Status: 	 Enabled
Driver: 	 AGPGART
AGP Rate: 	 8x
Fast Writes: 	 Disabled
SBA: 		 Enabled

```


FWIW, the frame rate for glxgears is the same ~1030fps using NvAGP 0, 1 or 2. However, I am not a gamer so do not really care.

> **orb9220 said:**
> using 5200 myself

Out of interest, what frame rate do you get from glxgears -printfps?

---

### Post by orb9220 on 2006-08-07
4837 frames in 5.0 seconds = 967.287 FPS
5476 frames in 5.0 seconds = 1095.135 FPS
5439 frames in 5.0 seconds = 1087.668 FPS
5484 frames in 5.0 seconds = 1094.679 FPS
5486 frames in 5.0 seconds = 1097.045 FPS
5457 frames in 5.0 seconds = 1091.232 FPS

---

### Post by plb on 2006-08-09
thanks that seemed to work.

---

### Post by Cariboo1938 on 2006-11-22
Hi all,
I'm not sure if I'm at the right place here, because my problem is not a blank screen but I have the same videa card which I think is not working properly. 
I updated the firmware of my optical drive LG GSA-4160B to version A306 and since then I can't play DVD movies anymore.
The DVD gets mounted (Icon appears at the desktop), but the player won't start anymore.
Has someone an idea what could be wrong? Do I need to get another driver?

---

