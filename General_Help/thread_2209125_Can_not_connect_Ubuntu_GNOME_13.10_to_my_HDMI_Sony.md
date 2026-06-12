---
title: "Can not connect Ubuntu GNOME 13.10 to my HDMI Sony Bravia TV"
date: 2014-03-04
forum: General Help
---

### Post by amjjawad on 2014-03-04
Hi,

Whenever I connect my laptop (with HDMI port) to my 32" LCD Sony Bravia, using:

Lubuntu
and
Xubuntu

It works just fine, sometimes with very few change in settings and everything is okay.

I have converted the laptop number 34 in my neighbourhood to Linux (Ubuntu GNOME 13.10). The user reported to me that she can't connect her laptop to her TV.

I'm now typing this from my laptop that has HDMI port, sitting in front of my 32" LCD Sony and indeed, I am having the very same issue she described.

This is all what I get:

[ATTACH=CONFIG]250859[/ATTACH]


First, my LCD is 32" not 72" :)

Second, I see odd stuff like:

A- On the LCD, after I connect the HDMI cable, I see ONLY the wallpaper of my Ubuntu GNOME 13.10 desktop. It does not matter what I try to open, there will be nothing on the LCD.

B- The mouse on my laptop is not synch with the LCD. Meaning, on my laptop, when I point the mouse somewhere, on the LCD, it goes to somewhere else and not at the same place where I'm pointing on my laptop. It seems that it is detecting two monitors at the same time and point the mouse at different places. That never happened with me with Lubuntu and Xubuntu before IIRC.


I managed to get a sound on the 32" LCD from the settings. However, I can't for example see the Activity Bar nor the panel at the top, nothing at all.

I don't know how to explain that better but it seems the system is detecting two different output device (monitor) and it is dealing with these different monitors (output devices) in two different way.
What it is showing on the built-in one, is different than what it is showing on the external one (32" LCD).

Thoughts?

I'm not using any PPA, this is a standard Ubuntu GNOME 13.10 installation.

Thank you!

---

### Post by amjjawad on 2014-03-04
[ATTACH=CONFIG]250860[/ATTACH]

Ok, that was super quick :D

I managed to see everything now on the LCD by doing the above (disable the built-in display).

Now, it seems I can't reverse that. When I do, I see nothing on my laptop display except the wallpaper I use and that is all.

So, I need now to figure out how to reverse which means, when I disconnect the HDMI cable, the built-in display should show the desktop and give the control back to the built-in one.

Needless to say, that process was a lot easier with Lubuntu and Xubuntu.
There must be an easier way to do all that without changing the settings, etc.

---

### Post by xeonix on 2014-03-04
@OP:

I had the same issue with my sony bravia, I guess it was not sync, I mean, I faced the same issues, when i tried to connect the laptop to TV, while my lapop was already powered-on/user is logged in.
I did a restart, and everything was fine.

---

### Post by amjjawad on 2014-03-04
Ok, I guess I figured out what is going on.

Case A:
To use the built-in display, I need to go to Display settings and disable the external one by selecting it and choose "Off". Then Apply.

Case B:
To use the external display, I need to go to Display settings and disable the internal (built-in) display by selecting it and choose "Off". Then Apply.

Sadly, there is no Case C where I can use BOTH at the same time.

Any idea how can I use both at the same time? without the need to keep doing the switch thing?

---

### Post by freebird54 on 2014-03-04
I use a Sony Bravia too - but mine is 40" (and it reports as 72" as well!).  However - you do not specify the laptop you are using, or its specs - in particular resolution.  It is possible that it cannot run separate resolutions at the same time with the same hardware :)

It occurs to me that would explain the output not reaching out to the edges of the TV when both are active?

Cure... is it possible for your laptop to accept a lower res when you want both to be powered?

Just a point to ponder...

---

### Post by amjjawad on 2014-03-04
Hi and thanks for posting :)

> **freebird54 said:**
> I use a Sony Bravia too - but mine is 40" (and it reports as 72" as well!).  However - you do not specify the laptop you are using, or its specs - in particular resolution.  It is possible that it cannot run separate resolutions at the same time with the same hardware :)

My Laptop is:
Lenovo G570 - Intel Core i5 2nd generation - 8GB RAM. This is the full details:


```
description: Notebook
    product: 20079 (HuronRiver_CRB)
    vendor: LENOVO
    version: Lenovo G570
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=IDEAPAD sku=HuronRiver_CRB uuid=6FDFC1DF-C571-11E0-983A-B870F43693F8
  *-core
       description: Motherboard
       product: Base Board Product Name
       vendor: LENOVO
       physical id: 0
       version: Base Board Version
       serial: CB10004412
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 40CN24WW(V2.10)
          date: 06/28/2011
          size: 1MiB
          capacity: 2496KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273DH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 62650E02
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273CH0-CH9
             vendor: Samsung
             physical id: 2
             serial: 844016BE
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 2a
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
          slot: CPU1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 1333MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 2c
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 2d
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 2e
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
     *-cache
          description: L1 cache
          physical id: 2b
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:41 memory:d0604000-d060400f
        
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:d0600000-d0603fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:d0500000-d05fffff
           
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:d0400000-d04fffff
           
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        

```

I used to connect my laptop to my 32" LCD Sony Bravia but not any more. I did this today to help my neighbour and to try to understand what is going on with her as I thought when [I converted her to Ubuntu GNOME]("http://amjjawad.blogspot.com/2014/01/2014-report-project-convert-my.html"), I thought it would work out-of-the-box, just like Lubuntu and/or Xubuntu last time I checked both.

So, me and my neighbour are having the same issue with two different hardware. It seems it is a system issue not a hardware one. I could be wrong though.


>  It occurs to me that would explain the output not reaching out to the edges of the TV when both are active?
I don't think that is the main issue as far as I can tell. As per the test I did, it seems the system (Ubuntu GNOME) is not or can't (?) synch two dispalys at the same time. Meaning, only one display should be 'active' at a time. Which, if you ask me, not really helpful :(

>  Cure... is it possible for your laptop to accept a lower res when you want both to be powered?
If you take another look at the screenshots I added on my previous posts here, you may notice that the resoultion on both displays was the same. I did change it but that didn't fix anything. The only way I figured out so far to see something on the LCD is to diable the built-in display (the laptop's screen) and keep the external display (32" LCD Sony) On.

If I want to go back and use the internal (built-in) display, I have to disable the external one.

For me, I don't mind that if and only if I'm using the LCD but for newcomers to Linux, that definitely will not impress them. 34 laptops in my area have been converted and all happy users. This is one of the very very few problems that my neighbour has reported. You see, I want to impress them as much as I can and make them feel the difference between Microsoft Windows (which in most if not all the time, works out-of-the-box when using HDMI) and Linux.


> Just a point to ponder...

Appreciate your help :)
I think I will also contact Tim, our head of developers (Ubuntu GNOME) and see if he has an idea about this and will update this thread.

Thank you!

---

### Post by freebird54 on 2014-03-04
Drat - I knew it couldn't be that simple! (it was on my older lappy here - but not apparently relevant on newer stuff.

Only other thoughts..
1. do the screens sync at the same frequency? 60MHz is common, but not universal...
2. is there a VGA output that can be used instead?

Well - that's about it for my alleged help.  Good luck - and keep up the good work! (I have only done 4 conversions, all on desktops.  Nice not to have to do so many 'service calls' than when they were on MS!)

---

### Post by amjjawad on 2014-03-04
Hi,

> **freebird54 said:**
> Drat - I knew it couldn't be that simple! (it was on my older lappy here - but not apparently relevant on newer stuff.
We are all learning here so don't worry about it ;)

> Only other thoughts..
1. do the screens sync at the same frequency? 60MHz is common, but not universal...

I don't know, there was nothing on the settings window that refers to any frequency. I don't think this might prevent the desktop to show up :) if there is something to do with the frequency, then there would be nothing on the screen. Since there is a picture but just a wallpaper without icons, etc ... it means there is some kind of missing settings. That will be fixed (as explained) after disabling one of the displays.

>  2. is there a VGA output that can be used instead?
For me, I have. For my neighbour who I'm trying to help here, I don't think she has that cable. With VGA, you will get a picture without sound ;) so, either to use external speakers or enjoy the low quality of the laptop's speakers and that is not going to help, I'm afraid.

She wants to use the HDMI, not the VGA :)

> Well - that's about it for my alleged help.  Good luck - and keep up the good work! (I have only done 4 conversions, all on desktops.  Nice not to have to do so many 'service calls' than when they were on MS!)
Appreciate your help and don't worry about it :)

I have sent this thread to my team (Ubuntu GNOME), hope someone has another thought :)

Will sure keep converting people, that will never stop :D
34 laptops so far, thousands are left and yes, I will, watch me :D

---

### Post by nipn on 2014-03-04
I make the shortcut key CTRL+ALT+E to display on an external display

[FONT=courier new] xrandr --output LVDS1 --off --output VGA1 --auto[/FONT]

I make the shortcut key CTRL+ALT+I to display on an the internal display

[FONT=courier new]xrandr --output LVDS1 --auto --output VGA1 --off[/FONT]

xrandr [FONT=times new roman]outputs available displays[/FONT]

[FONT=courier new]$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 4096 x 4096
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 223mm x 125mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
[/FONT]

---

### Post by amjjawad on 2014-03-04
Hi,

My neighbour sent me a message saying she has no sound :(

[ATTACH=CONFIG]250864[/ATTACH]

This is yet another problem she reported.
I think she said that she got two TVs/LCDs and on one of these, she got a picture but couldn't on the 2nd one. 
On both displays, she got no sounds.

Her laptop is HP g6

If I couldn't help her online, maybe I need to visit her.

---

### Post by amjjawad on 2014-03-04
Hi,

I just got a reply from Tim (Ubuntu GNOME main Developer) and he said that is a bug and we need to file one.

So, I guess either I should go over her place and take the laptop or ask her to bring it to me.

I'm a bit worried that she might ask to replace the system since she said that she cares a lot about the HDMI and that is one of the most important things she always do with her laptop. 

Tim is great and can solve bugs quickly but we don't know yet how long that might take.

> -There are known issues with most if not all HDMI monitors not     reporting the correct physical size, there were some bugs (look for     "Huge fonts" issue) caused by this, but I believe they are fixed     now.
    - There was a bug that affect cloning displays, but that should be     fixed in mutter 3.10.4
    -Some GPU's (Mostly Intel I think) have a maximum possible width, in     this case side-by-side configuration won't work, but stacked     vertically (top/bottom) will.

Will keep everyone updated in case there is something new :)


_**Edit:**_
Whether the external monitor is HDMI or not, this bug will happen with any external monitor - see: [http://ubuntuforums.org/showthread.php?t=2208614](http://ubuntuforums.org/showthread.php?t=2208614)

---

