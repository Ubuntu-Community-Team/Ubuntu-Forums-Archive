---
title: "Am I using the nvidia drivers? Geforce mx150 - asus zenbook"
date: 2020-05-07
forum: General Help
---

### Post by romeozi2 on 2020-05-07
Hi There,


I searched for hours and tried several solutions but I'm still stuck and I'm not sure to have everything working properly.


The situation is the following:


**uname -a**


    Linux rocco 5.4.0-28-generic #32-Ubuntu SMP Wed Apr 22 17:40:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


Ubuntu 20.04




The driver seems installed correctly


**lsmod | grep nvidia**


    nvidia_uvm            966656  0
    nvidia_drm             45056  0
    nvidia_modeset       1114112  1 nvidia_drm
    nvidia              20430848  2 nvidia_uvm,nvidia_modeset
    drm_kms_helper        184320  2 nvidia_drm,i915
    ipmi_msghandler       106496  2 ipmi_devintf,nvidia
    drm                   491520  13 drm_kms_helper,nvidia_drm,i915




**prime-select query**


    nvidia




**sudo lshw -c display**


    *-display                 
           description: VGA compatible controller
           product: UHD Graphics 620
           vendor: Intel Corporation
           physical id: 2
           bus info: pci@0000:00:02.0
           version: 07
           width: 64 bits
           clock: 33MHz
           capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
           configuration: driver=i915 latency=0
           resources: irq:127 memory:ed000000-edffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
      *-display
           description: 3D controller
           product: GP108M [GeForce MX150]
           vendor: NVIDIA Corporation
           physical id: 0
           bus info: pci@0000:01:00.0
           version: a1
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list rom
           configuration: driver=nvidia latency=0
           resources: irq:16 memory:ee000000-eeffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:ef000000-ef07ffff




**inxi -Fxx**




    Device-1: Intel UHD Graphics 620 vendor: ASUSTeK driver: i915 v: kernel bus ID: 00:02.0 chip ID: 8086:5917 
               Device-2: NVIDIA GP108M [GeForce MX150] vendor: ASUSTeK driver: nvidia v: 440.64 bus ID: 01:00.0 chip ID: 10de:1d10 
               Display: x11 server: X.Org 1.20.8 driver: none compositor: gnome-shell resolution: 1920x1080~60Hz, 1680x1050~60Hz 
               OpenGL: renderer: Mesa Intel UHD Graphics 620 (KBL GT2) v: 4.6 Mesa 20.0.4 direct render: Yes 




**lspci -v | grep 3D**


    01:00.0 3D controller: NVIDIA Corporation GP108M [GeForce MX150] (rev a1)
    	Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
    	Memory at e0000000 (64-bit, prefetchable) [size=32M]


**nvidia-smi**


    Thu May  7 23:18:08 2020       
    +-----------------------------------------------------------------------------+
    | NVIDIA-SMI 440.64       Driver Version: 440.64       CUDA Version: 10.2     |
    |-------------------------------+----------------------+----------------------+
    | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
    |===============================+======================+======================|
    |   0  GeForce MX150       Off  | 00000000:01:00.0 Off |                  N/A |
    | N/A   45C    P0    N/A /  N/A |      0MiB /  2002MiB |      0%      Default |
    +-------------------------------+----------------------+----------------------+
                                                                                   
    +-----------------------------------------------------------------------------+
    | Processes:                                                       GPU Memory |
    |  GPU       PID   Type   Process name                             Usage      |
    |=============================================================================|
    |  No running processes found                                                 |
    +-----------------------------------------------------------------------------+




BUT:




**more /usr/share/X11/xorg.conf.d/10-amdgpu.conf**


    Section "OutputClass"
    	Identifier "AMDgpu"
    	MatchDriver "amdgpu"
    	Driver "amdgpu"
    EndSection




**nvidia-settings**


    ERROR: Unable to load info from any available system
    
    
    (nvidia-settings:5784): GLib-GObject-CRITICAL **: 23:19:26.837: g_object_unref: assertion 'G_IS_OBJECT (object)' failed


[enter image description here][1]




  [1]: [https://i.stack.imgur.com/MpEAc.png](https://i.stack.imgur.com/MpEAc.png)




I think I should have seen a list of options in this panel...


**optirun --status** does not say nothing
**chrome://gpu** is reporting only my Intel UHD Graphics 620


If I launch **glxgears** I cannot see any processes on nvidia-smi


At the end I'm not sure if I'm using the nvidia drivers or not.




Any suggestion would be appreciated :)


Many thanks

---

### Post by monkeybrain20122 on 2020-05-08
In the terminal type
```
glxinfo | grep OpenGL
```

The output will tell you.

You have two graphic cards, it has optimus so chances are the intel card is being used by default. In Windows it switches automatically to the Nvidia card when you use graphic demanding programs like playing a game. But in Linux I think you have to do it manually and there seem to be two ways to do it (using bumble bee or Nvidia prime). I never have an optimus machine so not sure how to do it but there are many instructions on the forum and the internet.

---

