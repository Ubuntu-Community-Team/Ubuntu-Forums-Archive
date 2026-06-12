---
title: "Computer reboots itself - Help please!"
date: 2007-10-06
forum: General Help
---

### Post by Agent23 on 2007-10-06
Hi. I've recently built a new computer and installed Kubuntu Gutsy 64 on it. I'm new to linux but it was working out nicely and looks great. Unfortunately I had to uninstall it due to a power problem with the computer. I don't think Gutsy was to blame and I suspect it's a hardware fault, but I'm not sure so I'd greatly appreciate any help anyone could give me to figure this out. I've scoured the internet and tried quite a few things already, but nothing's worked yet and most of the stuff I've found elsewhere relates to Windows.

What's happening is this: when the computer is shut down, it appears to shut down successfully and power off as you would expect, but after about 4 seconds it immediately starts up again as if I'd pressed Restart. A similar thing happens if I try to Hibernate the computer. If I put it into Suspend, the computer will not wake up at all and has to be switched off using the case switch, although it doesn't restart itself afterwards in this instance. Usually the computer will restart itself if I switch it off by holding in the case switch. Here's what I've tried to get it to shut down as it should:

Tried every possible combination of BIOS power settings - ACPI 2, ACPI APIC enabled/disabled etc. When ACPI is fully disabled none of the distros I've tried will boot properly, so it's hard to tell if that helps any.

Made sure the BIOS wasn't set to power on under any circumstances (APM).

Updated BIOS to latest version.

Tried powering down using terminal commands (poweroff and shutdown -h)

Reformated and re-installed Kubuntu Gutsy, followed by Ubuntu Feisty incase the Gutsy beta was to blame.

Booted up from a live CD (Fedora & Feisty) and tried shutting down from there.

Disconnected all hardware I possibly could, external and internal, and checked all connections.

Tested RAM with Memtest, and reseated each stick one at a time to check for bad RAM.

Tried a different PSU.

Disconnected case power switch and used the reboot switch to start up.

Reset CMOS on motherboard.

Reseated graphics card.

I don't have a spare graphics card, so I can't be sure that's not the problem, but I'm guessing it's the motherboard. Before I RMA it, I'd like to know if anyone has any better ideas or can think of any possible solutions I might have missed. I don't have much experience with this.

Here's the system specs: 
Intel Q6600
Asus P5K-E Wifi motherboard
Gigabyte nvidia 8600gt graphics card
2g ddr2 800 Crucial RAM
SATA DVD writer
IDE hard disk

Thanks

---

### Post by PmDematagoda on 2007-10-06
What are the options that can be used by the BIOS _only_ in order to turn the computer on?

---

### Post by Agent23 on 2007-10-06
> **PmDematagoda said:**
> What are the options that can be used by the BIOS _only_ in order to turn the computer on?
The BIOS gives the following options under the Power menu (hope this is what you're asking):

Restore on AC power loss.
Power on by RTC alarm
Power on by external modems
Power on by PCI devices
Power on by PCIE devices
Power on by PS/2 Keyboard

I've disabled all of those. Exit And Save Changes in the BIOS also causes a reboot of course, but there are no other options to turn the computer on as far as I am aware.

---

### Post by PmDematagoda on 2007-10-06
Really strange, usually such things are caused by the BIOS due to certain configurations. But did this start happening recently or just after the power failure?

---

### Post by Agent23 on 2007-10-06
> **PmDematagoda said:**
> Really strange, usually such things are caused by the BIOS due to certain configurations. But did this start happening recently or just after the power failure?
Sorry if I wasn't clear, but this didn't start happening after a power failure. It's been like this since I put the computer together for the first time a couple of days ago. With so many new parts it's hard to tell which one might be at fault, but I think I've eliminated all the obvious things and I'm at a complete loss now.

---

### Post by atlfalcons866 on 2007-10-07
Old hard drive? an old hard drive can do that when it starts getting bad sectors

---

### Post by Agent23 on 2007-10-07
Thanks for the suggestion atlfalcons866, but the problem isn't the hard drive either - I've tried unplugging it and booting from a live CD, and the computer still restarts itself when I shut it down.

---

### Post by wub on 2007-11-20
I know this isn't what you want to hear, but I have a Fujitsu laptop that is probably having the same problem.  

Fujitsu N3430, purchased 12/06, dual boot Ubuntu orig 6.10, now 7.04 (XP)
Intel chipset 945 GM graphics, wifi
Intel chipset 82801 GBM bus, hardrive controller, usb etc.
SATA hard drive (no problems).

I have had the following problem since the system was new, but only recently did I get a better grasp of the symptoms.  I have upgraded from the standard display driver to the restricted driver - no effect.

Symptoms:
When I'm ready to shutdown, I click the shutdown button.  The system appears to shutdown.  ALL the lights go off, everything gets quiet, and the system will cool down to room temperature if there is time.

However, at midnight, or a very few seconds afterward (I guess I should attach the relevant section of the syslog), it starts up automatically.  I cannot find anything related to any crontab that corresponds to this.  Naturally, being a laptop, if I do not take some sort of action the battery is drained by morning.  This has the effect of truly shutting the system down, but I am not really satisfied with this solution.

I also tried all BIOS setting changes I could find, and shutting down from console with -h and other switches.  Behavior is exactly the same as the "shutdown" button.

Main reason XP is still my dual boot option?  When I'm shutting down, first I reboot from Ubuntu to XP, then I shut down from there.  This does work.

I >could< pull the battery out after shutting down from Ubuntu, granted, but this is graceless, and I suspect replacing the battery after removing it would be the same as not removing it.  Untested.

---

