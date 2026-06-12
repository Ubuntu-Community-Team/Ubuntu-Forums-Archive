---
title: "[SOLVED] One too many CPU?"
date: 2007-10-02
forum: General Help
---

### Post by joddbeem on 2007-10-02
Hi guys. I am a newbie with linux and ubuntu, but been thru a couple of successful installations. No challange really and a lot faster than any XP installation I ever done. :D

But lets not dwell at whats good:
Feisty 7.04 (Live CD) After install, I also did an online update.
Asus P4P800
3.0 GHz
3 GB RAM (I have 4, but one of the things I tried was to take out the 4th...)

Problem is that start up and everything is extremely slow. This is the best MB configuration I have installed on, all others show excelent performance on a basic install.

Thru search I found simmilare problems: blacklist intel_rng, have no effect. (shows in some other tread as a problem with the MB)

To my surprise, when starting the System Monitor, it list TWO CPUs ? Can anyone give me any help on this, could this be the cause of poor performance. Both CPUs have a usage of 50% - 100% when idle...

I have tried to study the output of top, ps -A and dmesg, but I can't figure out what to look for or what to do.

I have gone thru the BIOS of MB several times, but none of my changes seems to help. I have of course no RAID setup.

tia

---

### Post by joddbeem on 2007-10-02
here some from dmesg:
[   33.503969] Enabling unmasked SIMD FPU exception support... done.
[   33.503976] Initializing CPU#0
[   33.504033] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   33.509421] Console: colour VGA+ 80x25
[   33.509731] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   33.510064] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   33.643530] Memory: 3106876k/3144384k available (1992k kernel code, 36156k reserved, 893k data, 328k init, 2226880k highmem)
[   33.643541] virtual kernel memory layout:
[   33.643542]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   33.643543]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   33.643544]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   33.643545]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   33.643546]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   33.643547]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   33.643548]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   33.643551] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   33.719736] Calibrating delay using timer specific routine.. 6001.69 BogoMIPS (lpj=12003383)
[   33.719778] Security Framework v1.0.0 initialized
[   33.719784] SELinux:  Disabled at boot.
[   33.719800] Mount-cache hash table entries: 512
[   33.719936] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   33.719945] monitor/mwait feature present.
[   33.719947] using mwait in idle threads.
[   33.719953] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   33.719956] CPU: L2 cache: 1024K
[   33.719959] CPU: Physical Processor ID: 0
[   33.719961] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   33.719972] Compat vDSO mapped to ffffe000.
[   33.719975] Remapping vsyscall page to ffffe000
[   33.719991] Checking 'hlt' instruction... OK.
[   33.735802] SMP alternatives: switching to UP code
[   33.736140] Early unpacking initramfs... done
[   34.261160] ACPI: Core revision 20060707
[   34.261358] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   34.266978] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[   34.266997] SMP alternatives: switching to SMP code
[   34.267085] Booting processor 1/1 eip 3000
[   34.277376] Initializing CPU#1
[   34.354844] Calibrating delay using timer specific routine.. 5997.59 BogoMIPS (lpj=11995187)
[   34.354854] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   34.354861] monitor/mwait feature present.
[   34.354867] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   34.354870] CPU: L2 cache: 1024K
[   34.354873] CPU: Physical Processor ID: 0
[   34.354875] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   34.355148] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[   34.355190] Total of 2 processors activated (11999.28 BogoMIPS).
[   34.355317] ENABLING IO-APIC IRQs
[   34.355496] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   34.502651] checking TSC synchronization across 2 CPUs: passed.
[    0.003988] Brought up 2 CPUs
[    0.172487] migration_cost=226
[    0.172773] Booting paravirtualized kernel on bare hardware
[    0.172853] Time: 21:40:11  Date: 09/01/107
[    0.172883] NET: Registered protocol family 16
[    0.172972] EISA bus registered
[    0.172977] ACPI: bus type pci registered
[    0.173038] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.173041] PCI: Using configuration type 1
[    0.173043] Setting up standard PCI resources
[    0.188709] ACPI: Interpreter enabled
[    0.188712] ACPI: Using IOAPIC for interrupt routing
[    0.190067] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.190075] PCI: Probing PCI hardware (bus 00)
[    0.190747] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.190752] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.190989] Boot video device is 0000:01:00.0
[    0.191252] PCI: Transparent bridge - 0000:00:1e.0
[    0.191279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.203384] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.211754] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.212038] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.212325] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.212606] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.212888] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.213164] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.213448] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.213728] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.213836] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.213848] pnp: PnP ACPI init
[    0.220327] pnp: PnP ACPI: found 13 devices

---

### Post by MrHippocampus on 2007-10-02
Your cpu probably has hypertheading, this manifests itself as two cpu's in system monitor even though theres only one real cpu.

---

### Post by Arwen on 2007-10-02
I have Pentium 4 @3GHz 64bit that supports hyperthreading and feisty shows 2 cpus so maybe that's way yours shows 2,too.The only thing I can advise you is to try with 1GB only..At least mine works perfect..Good luck!

---

### Post by anaconda on 2007-10-02
If I understood correctly you have a Pentium4 processor, which has just one core.

This might be of interest: 

[http://ubuntuforums.org/showthread.php?t=471504](http://ubuntuforums.org/showthread.php?t=471504)

And no. it shouldn't slow things down.

The same thing confused me too. And for a while I used a 386 kernel, which doesnt support  dual core processors. The difference wasn't big, but it might have been a bit faster..

---

### Post by joddbeem on 2007-10-02
Thx, I didn't know it would show like that, I have Hyper Threading :D


I look for other things then.

---

### Post by Soybean on 2007-10-02
> **joddbeem said:**
> Both CPUs have a usage of 50% - 100% when idle...

Well, we've established that the 2 CPUs is normal, but 50% use when idle probably means something is going on.

Try this command:
```
ps -e -o pcpu,comm --sort pcpu
```

That will list all processes running on your computer, sorted by the percent of the CPU they're using. In theory, the last item on that list (the biggest CPU user) should be the cause of your problem. If you post the last 3-4 lines of output from that, maybe someone will have some more ideas. :)

---

### Post by joddbeem on 2007-10-02
Thx
Here is the last lines as mentioned above. 

2.9 nautilus
 3.2 gedit
 3.7 gnome-panel
 8.6 Xorg
10.0 hald

edit: I tried to kill hald, it seemed a little bit faster, but still sluggish, and I really don't know what I'm doin... CPU usage when starting system monitor still high. New ps... list Xorg at top(bottom).

---

### Post by Soybean on 2007-10-02
Hmm. Are you running Beryl or Compiz, or do you have Desktop Effects enabled? That's the only thing I've ever done that's gotten Xorg to constantly strain the processor.

Also, do you have any unusual hardware connected? "hald" is related to hardware support, and I'm pretty sure it's not supposed to be working that hard.

---

### Post by joddbeem on 2007-10-02
This is a clean install from last night, the install as well took some pretty long time, in compare with my other computers, (older ones), it took about 3 - 4 hours :D

Before that I tried to install on a IDE disk, I interupted this as I thought the time indicated some errors. This time I used SATA disk with an fresh XP install from last night as well. 200 GB disk w/3 partitions + swap

---

My Nvidia Gfx card has worked perfectly with same ubuntu on another MB.

MB has some features, but I turned of RAID in BIOS, nothing yet connected, still not closed the cover ;)

update: I tried to check for Desktop Effects, was told to update Gfx driver, did so, warned against properitare drivers or something, killed hald again, but not really impressed - way too slow. Restart to Desktop about 9:30 minutes

---

### Post by dabl on 2007-10-02
hald runs hardware interfaces for the USB bus, among other things -- I don't think you want to kill the daemon, or there won't be any plugging or playing on your system.

But, it shouldn't be using so much of your CPU -- sounds like something is continuously being "recognized", but not correctly, or there's some kind of conflict on a bus.  You might try unplugging things like webcams, scanners, memory card readers, thumb drives, etc., one at a time, and then rebooting and see if you suddenly find the problem goes away.  :)

---

### Post by joddbeem on 2007-10-02
I see your point, my killing of hald and other proc is just experimental or diagnostic, to see if something changes.

My keyboard and mouse, is a logitech usb type. There is nothing else connected, I need the computer up and running before trying to connect other stuff.

---

### Post by Soybean on 2007-10-02
Well... do you have a different keyboard and/or mouse you could try, just to see what happens? 

It's very likely that it's some sort of "hardware thing." Now you just need to figure out exactly which bit of hardware, and then try to make it work properly. I'm suggesting the mouse/keyboard because they're probably the easiest to test, if you happen to have spares nearby.

Another possible culprit is ACPI. You mentioned that it's a different motherboard from what you've used before, and power management is notoriously flaky. So you could try booting with "acpi=off" to see if it fixes the problem... if it does, then you'd know where the problem was, and you could turn it back on and try to narrow things down further.

---

### Post by joddbeem on 2007-10-02
:D Thx to all for the support :D

So glad to report that it seems my problem been solved. Due to the crowded placement of RAM vs AGP card, I took out the RAM as a last choice, I now run on 2 GB and boot takes just a few secounds. 

To help others with same I wrap it up here:

I wonder if this MotherBoard: Asus P4P800-E Deluxe, has some problems with adressing the RAM correctly. When there is 4 GB installed, system only report just above 3GB. However, to take advantage of Dual Channel RAM, if not paired with identical modules it's single channel. When I reduced it to 2 modules of 1 GB each it just fired up like one of those NASA rockets :)

This is other things I've done, they didn't help at the time of doing, but they may help in total, I will at a later point revert them and see if it works still.

In /boot/grub/menu.lst         to the kernel line I added:
[B]irqpoll
pci=noacpi
acpi=off
[/B]
I set my** DVD Burner to Cable Selec**t and not Master.
I unplugged all things USB but my Keyboard/Mouse.
I unplugged floppy.
I even took out all cables, as they where new and untested...

It's all tips and tricks I picked up in a lot of searches, fixed in newer distros I believe.

And again, thankfull for all help.

---

### Post by fjgaude on 2007-10-03
So happy this issue has been solved. Bravo!

---

