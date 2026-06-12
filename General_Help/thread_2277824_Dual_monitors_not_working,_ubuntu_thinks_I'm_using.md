---
title: "Dual monitors not working, ubuntu thinks I'm using laptop"
date: 2015-05-11
forum: General Help
---

### Post by Matthew_Rogers on 2015-05-11
I know there are many places online with this issue, but so far I've yet to find a working solution. So here is my problem, first I installed ubuntu 14.04 but switched to 12.04 as 14.04 would never load past the purple screen after the grub (even when trying nomodeset). Now 12.04 works fine, minus some start up errors as it thinks my hdd is a sdd, but thats another story. My problem is that I have 2 monitors, which I use frequently, but ubuntu won't recognize my second monitor, and for the first monitor, the display settings say I'm on a laptop and my max resolution is 1280x1024 when in fact both my monitors are 1920x1080.

Here is the output from running the terminal command xrandr:
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected primary 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  

```

Here is the output from running the terminal command "lspci | grep -i vga":
```

01:00.0 VGA compatible controller: NVIDIA Corporation Device 13c0 (rev a1)

```

And finally here is the output from the command "sudo lshw -C video":
```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff

```

I have a gtx 980 if that helps any. I also read somewhere to use nvidia-settings, which I tried, but perhaps I need to do something special? All I read was to use it and save the configuration to a file, so I did that after selecting all the options under the programs tab "nvidia-settings Configuration"

Does anyone have a possible solution for this?

---

### Post by jerryferry on 2015-05-12
I've run dual monitors for a couple of years. Tried it on various distributions. (I have heard that unity does not work well with dual monitors)
I have never got things to work successfully until the Nvidia drivers had been properly installed. On some failed installations I would have an "nvidia-settings" in the menu. Nothing worked properly until after installation - I had "NVIDIA X Server Settings" in my Administration menu. From there "X Server Display Configuration" and my GTX  650 works well with two different monitors. This was achieved with system tools/preferences -additional hardware.  I'm using 14.04 now, I think -from memory jockey in terminal may bring this up on 12.04? Hope this helps a bit.

---

### Post by Matthew_Rogers on 2015-05-12
> **jerryferry said:**
> I've run dual monitors for a couple of years. Tried it on various distributions. (I have heard that unity does not work well with dual monitors)
I have never got things to work successfully until the Nvidia drivers had been properly installed. On some failed installations I would have an "nvidia-settings" in the menu. Nothing worked properly until after installation - I had "NVIDIA X Server Settings" in my Administration menu. From there "X Server Display Configuration" and my GTX  650 works well with two different monitors. This was achieved with system tools/preferences -additional hardware.  I'm using 14.04 now, I think -from memory jockey in terminal may bring this up on 12.04? Hope this helps a bit.

I wish I could use 14.04 but I can't get that to work. But I checked the additional drivers/hardware like you suggested but it didn't detect anything. And I installed nvidia-settings but I do not have this "X Server Display Configuration" you mention

---

### Post by marco-zabot on 2015-05-14
I have a dual monitors working, Ubuntu 14.04 (compiz).
If can help, here the output:

$ xrandr
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 8192 x 8192
DVI-I-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0  
   720x400        70.1  
DVI-I-2 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+
   1680x1050      59.9  
   1280x1024      60.0  
   1440x900       59.9  
   1280x800       59.9  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0  
   720x400        70.1  
HDMI-1 disconnected (normal left inverted right x axis y axis)


$ lspci | grep -i vga
03:00.0 VGA compatible controller: NVIDIA Corporation GF106 [GeForce GTS 450] (rev a1)


$ sudo lshw -C video
[sudo] password for marco: 
  *-display               
       description: VGA compatible controller
       product: GF106 [GeForce GTS 450]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:75 memory:f8000000-f8ffffff memory:d8000000-dfffffff memory:d4000000-d5ffffff ioport:cc00(size=128) memory:fbc00000-fbc7ffff

---

