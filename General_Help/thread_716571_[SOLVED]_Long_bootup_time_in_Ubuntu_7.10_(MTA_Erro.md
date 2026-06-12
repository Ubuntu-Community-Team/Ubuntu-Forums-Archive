---
title: "[SOLVED] Long bootup time in Ubuntu 7.10 (MTA Error)"
date: 2008-03-06
forum: General Help
---

### Post by praveenpious on 2008-03-06
I find that its taking much time than earlier to boot into the desktop. On closer inspection, i find the following. Soon after i select the OS (ubuntu), an ubuntu loading bar shows up, when that bar is about to be filled, the interface changes to DOS mode and it shows the following message "Starting MTA". On displaying this, it just hangs and after about two minutes later it boots into the desktop. On googling i came to know its something termed Mail Transfer Agent.

I remember the problem began since i started using Cron/gnome-schedule for scheduling downloads.

What can be done to avert that message while booting up?

---

### Post by Arthur Archnix on 2008-03-06
Try to locate the error logs for MTA. You can look in /var/logs/

Also, post the output of 
> dmesg | tail --lines=20

Once you get this straightened out, and it boots up normally again. The next time you boot into ubuntu, instead of selecting ubuntu and hitting enter to boot, press 'e' to edit. Then go to the kernel line and press 'e' again. Then go to the end of the line and add 'profile' without quotes. Then press 'enter' and 'b' to boot. 

It will take a long time to boot up this once, but subsequent boot times should be improved.

---

### Post by praveenpious on 2008-03-06
The output of dmesg | tail --lines=20 is ```
praveen@praveen-desktop:~$ dmesg | tail --lines=20
[   37.520573] input: Power Button (FF) as /class/input/input4
[   37.526824] ACPI: Power Button (FF) [PWRF]
[   37.576024] input: Power Button (CM) as /class/input/input5
[   37.582291] ACPI: Power Button (CM) [PBTN]
[   37.600156] No dock devices found.
[   40.915266] eth0: no IPv6 routers present
[  100.549257] Failure registering capabilities with primary security module.
[  102.115975] [drm] Initialized drm 1.1.0 20060810
[  102.233626] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[  102.237475] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[  104.449890] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  104.450073] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  104.450228] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  104.805688] [drm] Setting GART location based on new memory map
[  104.805703] [drm] Loading R200 Microcode
[  104.805759] [drm] writeback test succeeded in 1 usecs
[  159.522628] PPP generic driver version 2.4.2
[  159.559354] NET: Registered protocol family 17
[  159.617648] NET: Registered protocol family 24
[  162.906930] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by Arthur Archnix on 2008-03-06
Unfortunately there's nothing in there that will help. No errors to speak of. We need to find out why its hanging at that point in the boot.

If I had to guess at this point I'd say it's because it's trying to do something over the network and it's not up yet. You can test this by configuring /etc/network/interfaces which should cause it to come up before the mta stuff.

I think all that's necessary is opening /etc/network/interfaces and changing "auto lo" to "auto eth0" or whatever you wired connection device name is. If it's wireless then its a bit more complicated, and I'd suggest plugging it in to your router or what have you for the purpose of this troubleshooting test.

---

### Post by praveenpious on 2008-03-06
Adding profile to the kernel command worked :)

Now its booting up faster, like it used to be. 

I checked for error logs, but couldnt find any messages pertaining to MTA.

Thanks mate. Problem solved :)

---

### Post by Arthur Archnix on 2008-03-06
:shock: oh.. umm :-k I mean.. good. Exactly as I intended. 8) 

Two things though: 

First, though I appreciate the thanks there's no need to thank every post. 

Second, it's good to mark your threads as solved once you figure them out. Makes searching for solutions easier. You can do this in thread tools.

Cheers,

---

### Post by chinaski on 2008-03-28
that did the trick for me too :guitar:

*thanks*

---

