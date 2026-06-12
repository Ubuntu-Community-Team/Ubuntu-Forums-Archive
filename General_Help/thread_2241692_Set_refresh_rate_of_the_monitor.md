---
title: "Set refresh rate of the monitor"
date: 2014-08-27
forum: General Help
---

### Post by renanrischiotto1 on 2014-08-27
Hello! I am needing to set the refresh rate of my monitor to 75Hz here in Ubuntu 14.04, how do?

Hugs!

---

### Post by TheFu on 2014-08-28
xrandr
arandr
lxrandr

Pick the one on your system. There may be a tool in the "display" settings manager - I don't use unity, so don't know how to get there. Sorry.

Also - trying to force a display rate that isn't supported can be bad for monitors.

---

### Post by renanrischiotto1 on 2014-08-29
Thanks for the reply! 
So, I would like to know how to change the refresh rate of the monitor in Unity :(

---

### Post by renanrischiotto1 on 2014-08-30
A little up

---

### Post by sbnwl on 2014-08-30
First check what frequencies are supported by your monitor,
Type the following in a terminal window and press enter:
```
xrandr
```

Check the output which will show the supported frequencies. The one with a * on it is the currently used one. Do not try to set a refresh rate which is unsupported by your monitor. You can also check the monitor documentation for supported refresh rates.
Let's assume we have to set the refresh rate to 60 Hz, along with the screen size as 1366x768.

Use the following command:
```
xrandr -s 1366x768 -r 60
```

It should be that easy.

---

### Post by renanrischiotto1 on 2014-08-30
At the moment I'm using Manjaro, because I need to use a 75Hz rate.

```
[renan@manjaro ~]$ xrandr
Screen 0: minimum 8 x 8, current 1440 x 900, maximum 8192 x 8192
DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 370mm x 230mm
   1440x900      59.89 +  74.98* 
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
[renan@manjaro ~]$ 
```

Don't work :(

```
[renan@manjaro ~]$ xrandr -s 1440x900 -r 59.89
Rate 59.89 Hz not available for this size
[renan@manjaro ~]$ xrandr -s 1440x900 -r 60
Rate 60.00 Hz not available for this size
[renan@manjaro ~]$ xrandr -s 1440x900 -r 75
Rate 75.00 Hz not available for this size
[renan@manjaro ~]$ xrandr -s 1440x900 -r 74.98
Rate 74.98 Hz not available for this size
[renan@manjaro ~]$
```

---

### Post by sbnwl on 2014-08-30
Well it worked for you one time.
Have you checked after logging off and logging again into your account? Or try to check after a reboot.

If the command is required again after each login, then try to put it in form of a startup script.

---

### Post by renanrischiotto1 on 2014-08-30
> Well it worked for you one time.
Have you checked after logging off and logging again into your account? Or try to check after a reboot.

No no, I had not done the procedure.

---

### Post by renanrischiotto1 on 2014-08-30
Even other resolution don't work:

```
[renan@manjaro ~]$ xrandr -s 1280x1024 -r 75.02
Rate 75.02 Hz not available for this size
[renan@manjaro ~]$ xrandr -s 1280x1024 -r 75
Rate 75.00 Hz not available for this size
[renan@manjaro ~]$ xrandr -s 1280x1024 -r 60
Rate 60.00 Hz not available for this size
[renan@manjaro ~]$ xrandr -s 1280x1024 -r 60.02
Rate 60.02 Hz not available for this size
[renan@manjaro ~]$
```

---

### Post by sbnwl on 2014-08-30
Do not delete your replies on the thread. It becomes confusing then to understand what has been done what not.

---

### Post by sbnwl on 2014-08-30
Does this work?```
xrandr -s 1280x960 -r 60
```

OR simply```
xrandr -s 1280x960
```

OR```
xrandr -r 60
```

---

### Post by renanrischiotto1 on 2014-08-30
```
[renan@manjaro ~]$ xrandr -s 1280x960 -r 60
Rate 60.00 Hz not available for this size
[renan@manjaro ~]$
```


Only the **xrandr -s [resolution]** works.

```
[renan@manjaro ~]$ xrandr -s 1280x1024
[renan@manjaro ~]$ xrandr
Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 8192 x 8192
DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 370mm x 230mm
   1440x900      59.89 +  74.98  
   1280x1024     75.02*   60.02  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
[renan@manjaro ~]$ xrandr -r 60
Rate 60.00 Hz not available for this size
[renan@manjaro ~]$ xrandr -r 60.02
Rate 60.02 Hz not available for this size
[renan@manjaro ~]$
```

---

### Post by renanrischiotto1 on 2014-08-30
> **sbnwl said:**
> Do not delete your replies on the thread. It becomes confusing then to understand what has been done what not.

Sorry, I edited because it did not work.

---

### Post by renanrischiotto1 on 2014-08-30
Well, I think I found out what was wrong. 


I reinstalled Ubuntu here, but before installing I entered the "live" mode and run the "xrandr -r 75" command, and it worked. So I proceeded with the installation, updated the system and installed the proprietary NVIDIA driver, and after I run the command again, but failed. Then I thought: "If in "live" mode work, and the system was using Nouveau, maybe if I go back to Nouveau works." Then I installed the Nouveau and done, it worked. But Nouveau in Ubuntu 14.04 is very bad here, slow. So I plugged the cable from my monitor to onboard video output and started Ubuntu. Again run the command xrandr and done, it worked. I researched it and discovered that the NVIDIA driver no longer works with xrandr (the interesting thing is that in Manjaro seems that worked with the NVIDIA driver, maybe he does not use xrandr to set the refresh rate of the monitor):


[https://bbs.archlinux.org/viewtopic.php?id=107923](https://bbs.archlinux.org/viewtopic.php?id=107923) 


Then the case was partially solved because I wanted to work with the NVIDIA driver (but okay, later I see it) and after the reboot, back to 60Hz rate, how to create a script to run every time the system starts?

---

### Post by TheFu on 2014-08-30
It appears from here there are multiple outputs for the card and the default is NOT the one you are using.  xrandr can set different resolutions and frequencies for each output - provided the command tell them to do so.

BTW - I stopped replying because you claimed to only want help with a GUI tool.  xrandr IS the tool for this stuff, as my initial post suggested. Beyond the 2 other GUI options, I haven't a clue what other tools may exist - outside the vendor specific ones from ATI and nvidia.

To learn all the options for it - **man xrandr** - there are many options.

---

### Post by renanrischiotto1 on 2014-08-30
> [COLOR=#000000]It appears from here there are multiple outputs for the card and the default is NOT the one you are using. xrandr can set different resolutions and frequencies for each output - provided the command tell them to do so.[/COLOR]

I do not quite understand that part, I was not using the default VGA?

> [COLOR=#000000]BTW - I stopped replying because you claimed to only want help with a GUI tool. xrandr IS the tool for this stuff, as my initial post suggested. Beyond the 2 other GUI options, I haven't a clue what other tools may exist - outside the vendor specific ones from ATI and nvidia.[/COLOR]

It's ok man, thanks :)

---

### Post by Bashing-om on 2014-08-30
renanrischiotto1; Hello;

Look. we can not help you if we do not know where you are at, or what you are doing.
At this time, let's get an idea of what you have installed hardware and software (modules) wise:
Post back the results:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display
dpkg -l  | grep nvidia

```
Now-a-days the monitor provides the EDID info and the kernel makes all the required adjustments. What makes you think there is a need to manually make these adjustments ? The driver is that interface between the kernel and your monitor.

Maybe, once we have a known condition
[INDENT][INDENT][INDENT]we can look at the situation
[/INDENT][/INDENT][/INDENT]

---

### Post by renanrischiotto1 on 2014-08-30
```
renan@ubuntu-desktop:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e32] (rev 03)
	Subsystem: ASRock Incorporation Device [1849:2e32]
	Kernel driver in use: i915
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
--
04:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] [10de:10c3] (rev a2)
	Subsystem: Point of View BV Device [1acc:85d3]
	Kernel driver in use: nouveau
04:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
renan@ubuntu-desktop:~$
```



```
renan@ubuntu-desktop:~$ sudo lshw -C display
[sudo] password for renan: 
  *-display               
       descrição: VGA compatible controller
       produto: GT218 [GeForce 8400 GS Rev. 3]
       fabricante: NVIDIA Corporation
       ID físico: 0
       informações do barramento: pci@0000:04:00.0
       versão: a2
       largura: 64 bits
       clock: 33MHz
       capacidades: pm msi pciexpress vga_controller bus_master cap_list rom
       configuração: driver=nouveau latency=0
       recursos: irq:46 memória:fd000000-fdffffff memória:e0000000-efffffff memória:de000000-dfffffff porta de E/S:ec00(tamanho=128) memória:feb00000-feb7ffff
  *-display
       descrição: Display controller
       produto: 4 Series Chipset Integrated Graphics Controller
       fabricante: Intel Corporation
       ID físico: 2
       informações do barramento: pci@0000:00:02.0
       versão: 03
       largura: 64 bits
       clock: 33MHz
       capacidades: msi pm bus_master cap_list rom
       configuração: driver=i915 latency=0
       recursos: irq:45 memória:fcc00000-fcffffff memória:c0000000-cfffffff porta de E/S:cc00(tamanho=8)
renan@ubuntu-desktop:~$
```



```
renan@ubuntu-desktop:~$ dpkg -l  | grep nvidia
rc  nvidia-331                                            331.38-0ubuntu7.1                                   amd64        NVIDIA binary driver - version 331.38
ii  nvidia-libopencl1-331                                 331.38-0ubuntu7.1                                   amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.38-0ubuntu7.1                                   amd64        NVIDIA OpenCL ICD
renan@ubuntu-desktop:~$
```

---

### Post by Bashing-om on 2014-08-30
renanrischiotto1; Hey ...

I may be way off base here. You are running Intel graphics:
> 
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e32] (rev 03)
	Subsystem: ASRock Incorporation Device [1849:2e32]
	Kernel driver in use: i915

Is this "integrated graphics" also a hybrid graphics situation ????
As how is that 'lspci' advises "kernel driver in use" i915 .... BUT 'lshw' says "configuração: driver=nouveau" for a  "produto: GT218 [GeForce 8400 GS Rev. 3".

Then given hybrid graphics are we not looking at using 
a) BumbleBee
b) Nvidia-Prime
To control the graphics ?

Switchable graphics:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

Will provide some guidance on which way you want to proceed.

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by renanrischiotto1 on 2014-09-01
> [COLOR=#000000]Then the case was partially solved because I wanted to work with the NVIDIA driver (but okay, later I see it) and after the reboot, back to 60Hz rate, **how to create a script to run every time the system starts?**[/COLOR]

?

---

### Post by renanrischiotto1 on 2014-09-01
I do not have a hybrid system, my motherboard is an ASRock G41C-GS with a onboard graphics chip Intel Graphics Media Accelerator X4500, with a offboard video card GT218 NVIDIA GeForce 8400GS Rev. 3 512MB.

> [COLOR=#000000]As how is that 'lspci' advises "kernel driver in use" i915 .... BUT 'lshw' says "configuração: driver=nouveau" for a "produto: GT218 [GeForce 8400 GS Rev. 3".[/COLOR]

I do not know what that means.

---

### Post by Bashing-om on 2014-09-01
renanrischiotto1; My thoughts:

> **renanrischiotto1 said:**
> 
I do not have a hybrid system, my motherboard is an ASRock G41C-GS with a onboard graphics chip Intel Graphics Media Accelerator X4500, with a offboard video card GT218 NVIDIA GeForce 8400GS Rev. 3 512MB.

As how is that 'lspci' advises "kernel driver in use" i915 .... BUT 'lshw' says "configuração: driver=nouveau" for a "produto: GT218 [GeForce 8400 GS Rev. 3".
I do not know what that means.


Well, what that means to me is that the system is in conflict; which card to use and the appropriate driver to load.
Does the system run on the Intel graphics with the i915 driver, or, does the system run on the Nvidia graphics with the open source driver nouveau ?
How to tell the kernel what to use, when. (???)

I think you are chasing your tail attempting to affect the resolutions for drivers that are not loaded.

Maybe in this situation BumbleBee will prove to be a good option.

[INDENT][INDENT]the good thing is that
[INDENT][INDENT][INDENT][INDENT]there are solutions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by renanrischiotto1 on 2014-09-01
Well, I did a new clean installation of Ubuntu with the cable connected to offboard card. Updated the system and installed the proprietary driver 331.38 (and after I installed my packages). Here is the result of the command **sudo lshw -c display**:```
renan@ubuntu-desktop:~$ sudo lshw -c display
[sudo] password for renan: 
  *-display               
       descrição: VGA compatible controller
       produto: GT218 [GeForce 8400 GS Rev. 3]
       fabricante: NVIDIA Corporation
       ID físico: 0
       informações do barramento: pci@0000:04:00.0
       versão: a2
       largura: 64 bits
       clock: 33MHz
       capacidades: pm msi pciexpress vga_controller bus_master cap_list rom
       configuração: driver=nvidia latency=0
       recursos: irq:45 memória:fd000000-fdffffff memória:e0000000-efffffff memória:de000000-dfffffff porta de E/S:ec00(tamanho=128) memória:fe000000-fe07ffff
renan@ubuntu-desktop:~$
```

**lspci -nnk | grep -iA3 vga**

```
renan@ubuntu-desktop:~$ lspci -nnk | grep -iA3 vga
04:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] [10de:10c3] (rev a2)
    Subsystem: Point of View BV Device [1acc:85d3]
    Kernel driver in use: nvidia
04:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
renan@ubuntu-desktop:~$
```

**dpkg -l  | grep nvidia**

```
renan@ubuntu-desktop:~$ dpkg -l  | grep nvidia
ii  nvidia-331                                            331.38-0ubuntu7.1                                   amd64        NVIDIA binary driver - version 331.38
ii  nvidia-libopencl1-331                                 331.38-0ubuntu7.1                                   amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                 331.38-0ubuntu7.1                                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver
renan@ubuntu-desktop:~$
```

---

### Post by Bashing-om on 2014-09-01
renanrischiotto1; Looks good

So far, are your graphics good now?
What now does the system see for hardware ?
```

lspci -nnk | grep -iA3 vga

```

Any solution
[INDENT][INDENT]is better than no solution
[/INDENT][/INDENT]

---

### Post by renanrischiotto1 on 2014-09-01
> [COLOR=#000000]So far, are your graphics good now?[/COLOR]

No, I'm still trying to set the refresh rate to 75Hz :(

> [COLOR=#000000]What now does the system see for hardware ?[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA3 vga[/FONT][/COLOR]
```[COLOR=#000000]
[/COLOR]
I posted above

---

### Post by Bashing-om on 2014-09-01
renanrischiotto1; Yeah !


That looks good too - I guess I am a victim once more of tunnel vision as I did not take notice of the 'lspci" output !

The tutorial to change the resolution is contained within:
[https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)
I expect will lead to good effect.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by renanrischiotto1 on 2014-09-01
> [COLOR=#000000]That looks good too - I guess I am a victim once more of tunnel vision as I did not take notice of the 'lspci" output ![/COLOR]

Sorry, here:

```
renan@ubuntu-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
04:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] (rev a2)
04:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
renan@ubuntu-desktop:~$
```

> [COLOR=#000000]The tutorial to change the resolution is contained within:[/COLOR]
[https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)
[COLOR=#000000]I expect will lead to good effect.[/COLOR]


I do not understand.

---

### Post by renanrischiotto1 on 2014-09-01
I opened a bug report:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1364199](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1364199)

---

### Post by renanrischiotto1 on 2014-09-03
So, without solution? =(

---

### Post by renanrischiotto1 on 2014-09-04
I opened a question too of the xorg package:

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/254081](https://answers.launchpad.net/ubuntu/+source/xorg/+question/254081)

---

### Post by renanrischiotto1 on 2014-09-04
Solved!

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/254081](https://answers.launchpad.net/ubuntu/+source/xorg/+question/254081)

---

### Post by Bashing-om on 2014-09-04
Great !

Appreciate you providing the solution .

There are those times it takes some one 
who does know.


Happy trails to you

---

