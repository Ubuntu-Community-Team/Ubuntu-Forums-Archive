---
title: "Updated Ubuntu 14.04 to latest update and screen blinks"
date: 2015-04-05
forum: General Help
---

### Post by Ralph L on 2015-04-05
I just applied all the latest updates (as of 4/3/2015) to my ubuntu 14.04 system, and now the screen blinks every few seconds.  Previously I had no blinking.  Anybody have any ideas of what is causing this, or what I can do about it?  The only thing I can think of is to format the ubuntu partition and reinstall everything--a fair amount of work, although my system before the update had few "added or changed features".  I think I had just added System Monitor, Synaptic, and maybe a few other things.

---

### Post by v3.xx on 2015-04-05
Did you do a kernel upgrade?  Can you revert to previous kernel at the grub boot window?  Worth a try :)

---

### Post by Bucky Ball on 2015-04-05
If you log out and back in is there still blinking? Does the machine blink no matter what or the blinking starts after you do something, suspend or put the computer to sleep, per chance?

---

### Post by Ralph L on 2015-04-06
Thanks to you guys for replying.
First, my computer is a Toshiba Satellite A215-S4697 with an AMD Turion 64 X2 Dual Core Mobile Technology TL52.  My graphic processor is RS690M [Radeon Xpress 1200/1250/1270] and the driver=radeon latency 64--this is from sudo lshw -C display.
Second, with the update I went from Linux 3.13.0-32-generic to Linux 3.13.0-48-generic.
Third, the blinking starts during the middle of booting--just after "Ubuntu" and several dots are displayed on the screen.  It happens no matter what is running, or if nothing is running.
If I logout and log back in, the blinking goes away. My error--the blinking persists.
If I boot from "Linux 3.13.0-48-generic (recovery mode)", and select "resume", when the recovery mode pauses, the blinking goes away, but the system runs very slow and the ratio of length to width on the screen is warped.  For example, round icons become oval--stretched horizantally.
If I boot up, suspend, and resume, the blinking persists.
If I boot from "Linux 3.13.0-32-generic" (the old system), there is no blinking.
Any help appreciated...

---

### Post by v3.xx on 2015-04-06
> If I boot from "Linux 3.13.0-32-generic" (the old system), there is no blinking.
Does this mean it boots to the desktop session?

From the description you gave, this sounds like nomodeset is needed.  Although I would not think nomodeset is necessary, I would give it a try anyhow.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Ralph L on 2015-04-06
v3.xx
Thank you very much for responding.  I tried setting "nomodeset" and it stopped the blinking, but videos ran very slowly and some of the displays had length to width ratios that were were warped.  "acpi_osi=" did not stop the blinking.  Any other thoughts?

---

### Post by Ralph L on 2015-04-07
I started from scratch, formatted the disk partition, installed the downloaded version of ubuntu 14.04 with the option to get updates checked, booted system (it was from Linux 3.13.0-32-generic) and there was no blinking.  Updated the system to the latest (as of 4/7/15) (it changed to Linux 3.13.0-48-generic), booted and there was the blinking again.  So there is something in the update (maybe something in Linux 3.13.0-48-generic) that is causing the issue.  This has become a real problem for me, as I need the latest version of 14.04 to be able to load large files from my new camera.  I really don't know where to turn at this point.  
Any help is REALLY appreciated.....

---

### Post by Ralph L on 2015-04-07
I looked at the dmesg log and found the following items that might be a problem:
```
[    0.168865] ACPI Error: No handler for Region [ERAM] (f5823f90) [EmbeddedControl] (20131115/evregion-162)
[    0.168872] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20131115/exfldio-299)
[    0.168879] ACPI Error: Method parse/execution failed [\_SB_.HTEV] (Node f5822e10), AE_NOT_EXIST (20131115/psparse-536)
[    0.168888] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node f582bd08), AE_NOT_EXIST (20131115/psparse-536)
[    0.171567] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.184051] ACPI: Interpreter enabled
[    0.184062] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.184069] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.184090] ACPI: (supports S0 S3 S4 S5)
[    0.184093] ACPI: Using IOAPIC for interrupt routing
[    0.184187] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.184383] ACPI: No dock devices found.
[    0.185361] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.185393] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.288564] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.288597] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.290279] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.290288] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.290347] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.292347] acpi PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.292352] acpi PNP0A08:00: host bridge window [mem 0x000d0000-0x000d1fff] (ignored)
[    0.292356] acpi PNP0A08:00: host bridge window [mem 0x000d2000-0x000d3fff] (ignored)
[    0.292360] acpi PNP0A08:00: host bridge window [mem 0x000d4000-0x000d5fff] (ignored)
[    0.292364] acpi PNP0A08:00: host bridge window [mem 0x000d6000-0x000d7fff] (ignored)
[    0.292368] acpi PNP0A08:00: host bridge window [mem 0x000d8000-0x000d9fff] (ignored)
[    0.292372] acpi PNP0A08:00: host bridge window [mem 0x000da000-0x000dbfff] (ignored)
[    0.292376] acpi PNP0A08:00: host bridge window [mem 0x000dc000-0x000ddfff] (ignored)
[    0.292379] acpi PNP0A08:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
[    0.292384] acpi PNP0A08:00: host bridge window [mem 0x40000000-0xdfffffff] (ignored)
[    0.292388] acpi PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff] (ignored)
[    0.292392] acpi PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.292396] acpi PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.292400] PCI: root bus 00: hardware-probed resources
[    0.292406] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-1a] only partially covers this bridge
[    0.292709] PCI host bridge to bus 0000:00
[    0.292714] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.292718] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.292722] pci_bus 0000:00: root bus resource [mem 0x40000000-0xfcffffffff]
[    0.292726] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.292738] pci 0000:00:00.0: [1002:7910] type 00 class 0x060000
[    0.292867] pci 0000:00:01.0: [1002:7912] type 01 class 0x060400
[    0.293010] pci 0000:00:05.0: [1002:7915] type 01 class 0x060400
[    0.293051] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.293126] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.293176] pci 0000:00:06.0: [1002:7916] type 01 class 0x060400
[    0.293218] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.293288] pci 0000:00:06.0: System wakeup disabled by ACPI
```

Also, here is the gpu Manager Log
```
[    0.168865] ACPI Error: No handler for Region [ERAM] (f5823f90) [EmbeddedControl] (20131115/evregion-162)
[    0.168872] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20131115/exfldio-299)
[    0.168879] ACPI Error: Method parse/execution failed [\_SB_.HTEV] (Node f5822e10), AE_NOT_EXIST (20131115/psparse-536)
[    0.168888] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node f582bd08), AE_NOT_EXIST (20131115/psparse-536)
[    0.171567] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.184051] ACPI: Interpreter enabled
[    0.184062] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.184069] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.184090] ACPI: (supports S0 S3 S4 S5)
[    0.184093] ACPI: Using IOAPIC for interrupt routing
[    0.184187] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.184383] ACPI: No dock devices found.
[    0.185361] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.185393] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.288564] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.288597] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.290279] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.290288] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.290347] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.292347] acpi PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.292352] acpi PNP0A08:00: host bridge window [mem 0x000d0000-0x000d1fff] (ignored)
[    0.292356] acpi PNP0A08:00: host bridge window [mem 0x000d2000-0x000d3fff] (ignored)
[    0.292360] acpi PNP0A08:00: host bridge window [mem 0x000d4000-0x000d5fff] (ignored)
[    0.292364] acpi PNP0A08:00: host bridge window [mem 0x000d6000-0x000d7fff] (ignored)
[    0.292368] acpi PNP0A08:00: host bridge window [mem 0x000d8000-0x000d9fff] (ignored)
[    0.292372] acpi PNP0A08:00: host bridge window [mem 0x000da000-0x000dbfff] (ignored)
[    0.292376] acpi PNP0A08:00: host bridge window [mem 0x000dc000-0x000ddfff] (ignored)
[    0.292379] acpi PNP0A08:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
[    0.292384] acpi PNP0A08:00: host bridge window [mem 0x40000000-0xdfffffff] (ignored)
[    0.292388] acpi PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff] (ignored)
[    0.292392] acpi PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.292396] acpi PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.292400] PCI: root bus 00: hardware-probed resources
[    0.292406] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-1a] only partially covers this bridge
[    0.292709] PCI host bridge to bus 0000:00
[    0.292714] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.292718] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.292722] pci_bus 0000:00: root bus resource [mem 0x40000000-0xfcffffffff]
[    0.292726] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.292738] pci 0000:00:00.0: [1002:7910] type 00 class 0x060000
[    0.292867] pci 0000:00:01.0: [1002:7912] type 01 class 0x060400
[    0.293010] pci 0000:00:05.0: [1002:7915] type 01 class 0x060400
[    0.293051] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.293126] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.293176] pci 0000:00:06.0: [1002:7916] type 01 class 0x060400
[    0.293218] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.293288] pci 0000:00:06.0: System wakeup disabled by ACPI
```

---

### Post by Bucky Ball on 2015-04-07
Have you tried a full update/upgrade? You never know, your issue might be known and fixed in the latest. Try:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report any and all errors and see if blinking persists ...

---

### Post by Ralph L on 2015-04-08
Bucky Ball
Will I end up with 14.04 LTS or 14.10, when I do the upgrade???  I want the Long Term Support.

---

### Post by Bucky Ball on 2015-04-08
14.04 LTS. The 'sudo apt-get dist-upgrade' and upgrade commands will ONLY upgrade your currently installed apps/software, if it needs it, NOT the OS. If anything needs upgrading you will be asked before the upgrade proceeds. ;)

Upgrading the OS can be done via the command line, but different command.

---

### Post by Ralph L on 2015-04-08
Bucky Ball,
Thanks.  I will give it a try.  It will be about a week before I have a chance to work on it again.  I'll tell you the results then.

---

### Post by Ralph L on 2015-04-17
Bucky Ball
I tried what you suggested to make sure I had the latest version of everything.  It didn't work.  The screen still blinks every few seconds--but randomly. I tried disabling unity by installing gnome-session-fallback. I tried both the classic login with compiz and the classic login with metacity.  Neither helped.  This makes sense as the blinking starts during boot as soon as the word Ubuntu and the row of dots appears, so I don't think either compiz or metacity was loaded at that point.  I am trying to figure out what could have been updated, dealing with displays during boot, after the original version of 14.04 that I downloaded.   
Can you think of anything else I could try???

Thanks for your help.

---

### Post by Bucky Ball on 2015-04-18
Well, I can say this. If different desktop environments make no difference then it is probably something with the kernel as they are all using the same one ...

---

### Post by Ralph L on 2015-04-18
Apparently this is a well known problem with Toshiba Satellite A215-S4697 laptops:  [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1405277](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1405277) .  However, no solutions and priority rated as low......  I wonder if installation of the 64 bit version of 14.04 would help.  When I go to System Setting>Details, it says: OS type 32 bit.  After all this is a Turion 64 X2 Dual Core processor.  Any thoughts??

---

### Post by Bucky Ball on 2015-04-18
Then you should be using the 64bit, although unsure it will help with your issue. One way to find out. ;)

---

### Post by Ralph L on 2015-04-22
I solved the problem by upgrading the kernel in 14.04 to 3.19 as described here:  [http://www.linuxbsdos.com/2014/12/06/how-to-upgrade-ubuntu-14-10-kernel-to-version-3-17-1/](http://www.linuxbsdos.com/2014/12/06/how-to-upgrade-ubuntu-14-10-kernel-to-version-3-17-1/) and here:  [http://www.linuxbsdos.com/2014/12/06/how-to-upgrade-ubuntu-14-10-kernel-to-version-3-17-1/](http://www.linuxbsdos.com/2014/12/06/how-to-upgrade-ubuntu-14-10-kernel-to-version-3-17-1/)  Linux kernel 3.19 has the blinking problem fixed and so far I haven't had any problems with the newer kernel in the older system.  
However, what I did notice was that 14.04 seems to be a memory hog taking about twice as much memory just to run the operating system as 12.04 took.  On my 1GB laptop I was almost immediately seeing slow down and swapping to disk taking place.  I installed gnome-session-fallback to get rid of unity and notice that gnome-panel went from less than 10MB in 12.04 to more than 45MB in 14.04.  I also noticed that something with a name like evolution-calendar took up nearly 40MB and that it can't be removed.  Anyway, now I am looking at xubuntu to get the memory requirements down.

Thank you to everybody that helped me with this problem.  I really appreciate it.

---

### Post by Bucky Ball on 2015-04-22
Glad you got it solved.

I use a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") with only the apps I want/need. Perhaps you might consider going down that route to remove bloat and speed things up. ;)

Also, see [here]("http://www.psychocats.net/ubuntu/minimal").

---

