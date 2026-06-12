---
title: "Setting Screen Resolution"
date: 2015-09-23
forum: General Help
---

### Post by rbscairns on 2015-09-23
I recently installed Ubunut 14.04 as a dual boot system (with Windows XP) on my PC (1GB RAM, Intel® Atom CPU N270 @ 1.60GHz × 2, Intel 945GME x86/MMX/SSE2, 32 bit).

I wish to set my screen resolution to 1280x768 so a circle looks like a circle and not like an ellipse. Unfortunately, Ubuntu settings only gives me a choice of 1024x768 or 800x600 (unknown display and will not recognise the display). The display is an ASUS model VH202, version VH202T.

How can I set the screen resolution to 1280X768?

---

### Post by Bucky Ball on 2015-09-23
*Thread moved to **General Help**.*

Please provide the output of this command:

```
sudo lshw -C video
```

Have you done an update using Software Updater? Do that, then check Additional Drivers. Anything there pertaining to graphics? Let us know.

You can also try installing arandr from the repositories and giving that a go. See if that offers the correct resolution (right click on the graphic of the screen in arandr).

---

### Post by rbscairns on 2015-09-23
Output for sudo lshw -c video is

```
PCI (sysfs) 
```

My software is up-to-date. I checked additional divers when installing and there was nothing pertaining to graphics.

I installed and ran arandr. It returns a window sating VGA1

---

### Post by Bucky Ball on 2015-09-23
You didn't wait for long enough with the command. Run again and please wait after you get 'PCI (sysfs)'. 

I'm not talking about additional drivers while installing, I'm talking about looking for 'Additional Drivers' in the Dash now and looking at what's on offer.

Right click on the VGA window> Resolution> What options are there????

---

### Post by rbscairns on 2015-09-23
Sorry about that Bucky.

sudo lshw -c video returns:

```
 *-display:0             
       description: VGA compatible controller
       product: Mobile 945GSE Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fbd00000-fbd7ffff ioport:dc80(size=8) memory:d0000000-dfffffff memory:fbcc0000-fbcfffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fbd80000-fbdfffff
```

The Dash Additional Drivers shows "No additional drivers available." and "No proprietary drivers are in use."

In the arandr Screen Layout Editor the available resolutions are:

[INDENT]1028x768
800x600
849x480
640x480[/INDENT]

---

