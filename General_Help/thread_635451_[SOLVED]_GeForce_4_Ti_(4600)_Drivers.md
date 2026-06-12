---
title: "[SOLVED] GeForce 4 Ti (4600) Drivers?"
date: 2007-12-08
forum: General Help
---

### Post by a_pedestrian on 2007-12-08
[color=red]Result Of Thread:[/color] Virtual Machines don't support high-end graphics cards.

------------------------------------------------------------------------------------------------

Thanks a lot for any help with this, I've been at it for hours at this point.

I installed Kubuntu 7.10 and now would like to get my graphics accelerator working.  I went on NVidia's website [here](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html) and found that the GeForce4 Ti 4600 is supported by the 1.0-96xx driver.

So I downloaded NVIDIA-Linux-x86-1.0-9639-pkg1.run and ran it, and it says this:

```
WARNING: You do not appear to have an NVIDIA GPU supported by the 1.0-9639 
NVIDIA Linux graphics driver installed in this system.  For further details, please see the 
appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux 
driver download page at www.nvidia.com.
```

So I went to [this page](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9639/README/appendix-a.html) and it said the same thing - it should be supported by this driver.

So at this point I said to myself, "OK.  Maybe the documentation is wrong."  So I went to the site and used their wizard [here](http://www.nvidia.com/Download/index.aspx?lang=en-us) entering the following fields:

```
Product Type: Legacy
Product Series: GeForce4 Ti Series
Operating System: Linux 32-bit
Language: English (US)
```

Which yielded the driver number NVIDIA-Linux-x86-96.43.01-pkg1.run at [this page](http://www.nvidia.com/object/linux_display_x86_96.43.01.html).  So I downloaded that one and tried to install it, and I got this:

```
WARNING: You do not appear to have an NVIDIA GPU supported by the 96.43.01
 NVIDIA Linux graphics driver installed in this system.  For further details, please see the 
appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux 
driver download page at www.nvidia.com.
```

So at this point I said to myself, "WTF."

---

### Post by dcstar on 2007-12-08
> **a_pedestrian said:**
> Thanks a lot for any help with this, I've been at it for hours at this point.

I installed Kubuntu 7.10 and now would like to get my graphics accelerator working.
..........
So at this point I said to myself, "WTF."

Have you tried just installing the nvidia-legacy package?

---

### Post by a_pedestrian on 2007-12-08
Yes, nvidia-glx-legacy is already installed, but I still can't get the OpenGL screensavers (for instance) to display.

Any idea what's wrong?

---

### Post by a_pedestrian on 2007-12-08
No one has any clue about this?  It's driving me up the wall.

---

### Post by overdrank on 2007-12-08
> **a_pedestrian said:**
> No one has any clue about this?  It's driving me up the wall.

Hi and I have two of those GeForce4 Ti 4600 and one 4800. I have used Envy on all of the installs and Gutsy was working great until  I upgraded my card to a 6600 gt.

---

### Post by a_pedestrian on 2007-12-08
-snip- misunderstood post

---

### Post by a_pedestrian on 2007-12-08
It's telling me I need a bunch of dependecies in dpkg now, is that normal?

---

### Post by overdrank on 2007-12-08
> **a_pedestrian said:**
> -snip- misunderstood post

Hi and excuse me but I was not able to read your replies before your edit. Did I miss something? :confused:

---

### Post by a_pedestrian on 2007-12-08
OK.

Installed it, got the dependecies with apt-get --install

Now I have a new problem (sorry for all this).

ENVY ERROR: Nvidia card not found

in /var/log/envy-installer.log

(This is in the automatic installer, the manual installer works, but has dropped me to a commandline-only interface, give me a minute to fix that.)

---

### Post by a_pedestrian on 2007-12-08
This is insane.  Envy doesn't work, legacy drivers don't work, the reccomended drivers don't work WTF IS GOING ON.

---

### Post by overdrank on 2007-12-08
> **a_pedestrian said:**
> This is insane.  Envy doesn't work, legacy drivers don't work, the reccomended drivers don't work WTF IS GOING ON.

Ok lets start at the beginning. Please post the output of the command ```
lspci
``` in the terminal.

---

### Post by a_pedestrian on 2007-12-08
```
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
```

I guess I should have started out by thinking "Maybe the virtualization is getting in the way" but (in addition to the fact that I didn't know until now to check for things like this with lspci) it just seemed so unlikely that when all the other peripherals were working perfectly right out of the box, that any problems would arise with the graphics card.

Is there a remedy for this do you think, that would let me keep virtualizing, or am I just screwed until I wipe out the computer completely with a reformat?

---

### Post by overdrank on 2007-12-08
> **a_pedestrian said:**
> ```
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
```

I guess I should have started out by thinking "Maybe the virtualization is getting in the way" but (in addition to the fact that I didn't know until now to check for things like this with lspci) it just seemed so unlikely that when all the other peripherals were working perfectly right out of the box, that any problems would arise with the graphics card.

Is there a remedy for this do you think, that would let me keep virtualizing, or am I just screwed until I wipe out the computer completely with a reformat?

Hi and yes the virtual system info would have helped just a bit. There is no way that I know of to install the graphic driver while using it as a virtual machine. You could dual boot with window and get the full effect. :KS

---

### Post by a_pedestrian on 2007-12-08
Thanks a lot for your help and patience, I guess I'm just going to have to live with low fps.

---

