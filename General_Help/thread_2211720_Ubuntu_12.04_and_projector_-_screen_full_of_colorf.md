---
title: "Ubuntu 12.04 and projector - screen full of colorful lines"
date: 2014-03-17
forum: General Help
---

### Post by dadrlora on 2014-03-17
Firstly I am not a native speaker, so I apologize in advance for the mistakes when writing.

I have a problem because the projector that is connected to my computer does not display properly. At my workplace I use several types of projectors and some work as expected, while others do not even recognize my computer. I tried to System Settings -> Displays -> Detect Displays but only is displayed Laptop
My computer is a laptop Fujitsu Siemens Amilo Li1705 with dual boot Ubuntu 12.04 and WinXP.
Here I will describe what happens when the computer is connected to some of these projectors that do not show the image properly (or at all).
When I start the computer projector is connected and turned on and properly display the grub menu. Once I choose Ubuntu, the whole boot process is seen through the projector (even ubuntu logo) until the laptop does not show the login screen. Then the projector loses signal.


Here is the output of lspci | grep VGA

```

AMILOLi1705:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
AMILOLi1705:~$ 

```


Here is part of the output of lshw
```

 *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:c8000000-c8ffffff memory:a0000000-bfffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=16 mingnt=2
                resources: memory:a0000000-bfffffff memory:c8000000-c8ffffff

```

Here is the output of xrandr
```

AMILOLi1705:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1280x768       60.0  
   1280x720       59.0  
   1024x768       60.0  
   1024x600       59.0  
   1024x576       60.0  
   1024x512       60.0  
   800x600        60.0     56.0  
   720x576        60.0  
   856x480        60.0  
   848x480        60.0  
   800x480        60.0  
   720x480        60.0  
   640x480        60.0  

```


After a lot of reading on the forum I found out that my laptop uses vesafb framebuffer driver, so I tried to follow the instructions to activate the driver viafb and I managed but with limited success because now the projector shows an image that is full with colorful lines (opposed to nothing, this is progress). 

screenshot: [http://i58.tinypic.com/jfkbck.jpg](http://i58.tinypic.com/jfkbck.jpg)

(tested with the sudo modprobe viafb viafb_mode=640x480 viafb_bpp=16 viafb_refresh=60
I tried various values &#8203;&#8203;for viafb_mode and nothing works)

After activation viafb drivers on the laptop screen is also full of colorful lines, Ctrl + Alt + F1 on the laptop does not show anything, and the projector displays the image properly (text only)

My goal is to enable the projector to work using ubuntu, even at very low resolution, because otherwise I'm forced to do a presentation using windows, and I do not like that.

Thanks to all of you that read this treat, any idea will be apreciated.

---

