---
title: "How do I fix resolution in third monitor on Ubuntu 18.04?"
date: 2019-07-04
forum: General Help
---

### Post by dora5 on 2019-07-04
I added a third monitor to my multi-monitor setup, and it's using the i915 intel driver, appropriate since it's plugged into onboard graphics, and works fine except for the 1024 x 768 resolution; everything is huge and it doesn't work with the other monitors that are on an AMD Radeon card with radeon driver and have 1280 x 1024 resolution.   The monitors configured just fine; their order and which one is primary work perfectly.   1024 x 768 is the highest resolution that is available for this monitor.

I got it working just fine in Windows 7, but had to add the intel driver to get it to work.   I was having a similar problem before I installed the driver, but troubleshooting below makes it clear that Ubuntu is running the intel driver for the monitor that is plugged into the onboard graphics connector, and the radeon driver for the two monitors that are plugged into the radeon card, just as in Windows.  

Below is some of my troubleshooting output. 



Ubuntu 18.04.2 LTS
Memory 15.6 GiB
Intel Core i5-2400 CPU @ 3.10GHz x 4
Graphics AMD Cedar
Gnome 3.28.2
OS type 64 bit

The Radeon card is HD 5450.  The motherboard is DH67BL; it's a homebuilt system.   Ubuntu installed the i915 GPU driver on installation.  

The monitor that is plugged into the onboard graphics is also labelled Unknown, though the radeon driver calls the other 19" Dell monitor a 19" Dell monitor.  



glxinfo | grep OpenGL


vendor string:  X.Org
renderer string:  AMD CEDAR (DRM 2.50.0/4.18.0-25-generic, LLVM 7.0.0
core profile version string 3.3  Msa 18.2.8
version string  3.1 Mesa 18.2.8
profile shading language version string:  OpenGL ES GLSL ES 3.10

dora@dora-desktop-ubuntu:~$ sudo lshw -C video
[sudo] password for dora: 
  *-display                 
       description: VGA compatible controller
       product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:38 memory:e0000000-efffffff memory:f4920000-f493ffff ioport:e000(size=256) memory:c0000-dffff
  *-display
       description: Display controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:36 memory:f4400000-f47fffff memory:d0000000-dfffffff ioport:f000(size=64)



$ lspci -k | grep -EA3 'VGA|Display|3D'
00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
    Subsystem: Dell XPS 8300
    Kernel driver in use: radeon
    Kernel modules: radeon

xrandr basically tells me the information that is in graphics settings, plus vector and axis information I never needed to know.





Online research revealed that many people have been having this problem with Intel drivers and Ubuntu 18.04.  Is this the sort of Cannical failure to pay attention to Ubuntu that is driving the popularity of MX Linux?  Trust me, I'm going over there to find out if I'm going to run into this there if I install their version.  I saw "wait for Ubuntu or Intel to release updated drivers... no, I don't think so.   Ubuntu 18.04 is a year old, and, I need my setup to work now, not a few years from now.   Canonical is thinking what?!!!  It really does look as though they're about as committed to the future of Ubuntu as zit.  


I tried to update the driver, but, the up to date version of Intel's driver for this board has a whole bunch of requirements and dependencies, and not one of them still exist.  


I did run update and system upgrade, which I was informed should update the video driver, and the problem is not fixed, whether it really upgraded the video driver or not.


People have fixed the problem by messing with various configuration files, neither of which exist on my system, and no online information tells us where Ubunty 18.04 IS putting the graphics settings.   Where would that be, exactly?

After hours of jumping through hoops I succeeded in CREATING /etc/x11/xorg.conf, but after rebooting my system didn't write one piece of information in it, and there is no clear and complete description of what to write in it myself, only certain changes to make or chunks of code to add.   

The changes in the new version of Ubuntu are so bad, I was told, I have to use gksudo and not sudo or gedit, to avoid messing up my graphics, except, the command gksudo turned out not to exist.   And I was told to do ctrol-alt-F1 to get into  the terminal mode, which no longer works.  And tell it sudo x-configure or else sudo x -configure, I tried both, and that command doesn't exist either.   !!!!!!!!!!!!!!!  I have ten books on Linux, and Ubuntu, but none of the old commands still work, and I guess noone has bothered to publish what does.   


Can someone please tell me EXACTLY what to do to fix this problem, and I mean, EXACTLY what I need to put in what file, and how to do that.



Or, if I revert to Linux drivers, would I then be able to use Google EArth?   On my Dell 780, Core2Duo, I had to jump through hoops with a video card and drivers to get Google Earth to work.    Google Earth is important to my work.   



If I should change to Ubuntu's drivers, how do I do that?  I can't find instructions on how to do that anyplace, just lots of instructions on how to change from Ubuntu's drivers to Intel.   




Thanks!


Yours,
Dora Smith

---

### Post by CatKiller on 2019-07-04
First of all, calm down. I'm sure you're very frustrated, but that won't help. We're all just volunteers here, Ubuntu users like you. As calmly and methodically as you can, stepping through the problem is how things get fixed. 

> **dora5 said:**
> Can someone please tell me EXACTLY what to do to fix this problem, and I mean, EXACTLY what I need to put in what file, and how to do that. 

No. We aren't sitting with your hardware, seeing all the output and symptoms. We can offer guidance, the benefit of experience, and what knowledge we've built up. You're the one that has to actually get it done. 


> 1024 x 768 is the highest resolution that is available for this monitor.

I got it working just fine in Windows 7, but had to add the intel driver to get it to work.   I was having a similar problem before I installed the driver

This is the most important part of what you wrote.

It shows that your computer isn't receiving EDID. Either because your monitor isn't providing it, or it's not getting through whichever connection you're using, or because your graphics adaptor can't understand what it's been given.

When a display is initialised, it will provide a list of resolutions and timings that it can support. Without that information the display will be set to something known to be safe, to avoid damaging your monitor.

The easiest way to handle that, in my experience, is to grab the HorizSync and VertRefresh values from the monitor's manual or specifications and pop that into xorg.conf. That way, you're simply specifying the minimum necessary to make all the automatic stuff work.

A slightly more convoluted way is to use the cvt command to work out all the timings for a particular resolution at a particular refresh rate, and enter that as a full modeline in your xorg.conf.

Ideally you'll be able to have just a snippet to describe that one monitor in a file in /etc/X11/xorg.conf.d. That way you won't have to specify all the bits that go in an xorg.conf, and you won't need to recreate your multimonitor setup statically. To avoid the permissions problems that you get when using graphical programs with sudo you can use **sudo -H gedit /etc/X11/xorg.conf.d/20-nameyoucallyourmonitor.conf**. sudo nano would be fine, too, if you're comfortable with a command line text editor. 

Let us know where you've got to, and someone can help walk you through the next step.

---

