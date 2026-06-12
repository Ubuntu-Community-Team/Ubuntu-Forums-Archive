---
title: "Ubuntu freezes on startup during hard drive check"
date: 2008-04-16
forum: General Help
---

### Post by Atheil on 2008-04-16
I guess it's been 30 reboots since I've installed Ubuntu on my laptop, and I've had no problems until now. On startup, Ubuntu attempts to check dev/sda1 (which I assume is my primary HDD, and not my swap partition). When the forced check gets to about 70%, some times 73%, sometimes something in between, it freezes, and I can hear my HDD stop spinning. 

This happens every time I startup, and I have not been able to get onto my machine.

Some further information:

If I start up Ubuntu in recovery mode, it freezes at 
[        0.552000] ENABLING IO-APIC IRQs
[        0.552000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

I also notice though, that few lines behind this is the message:

[        0.456000] ACPI: Looking for DSDT in initramfs. . . error, file /DSDT.aml not found.

I assume that that is the error that's causing it. But I have no idea what it is, or what I should do about it. Any help would be greatly appreciated. I would prefer not to have to format this machine as it was almost impossible to get Ubuntu working on it, and it was only through luck and about 5 hours work that I got it on there.

---

### Post by wdaniels on 2008-04-16
The missing DSDT file should not be a problem - the kernel will just read the ACPI table from your hardware and the file is just a way to specify your own DSDT in case the one supplied by the OEM is buggy.  In any case this is for ACPI which has more to do with power management and similar functionality.  I don't see this having anything to do with your problem.

Unfortunately, I'm not much of an expert with such low-level problems, but I do have a couple of suggestions until someone with more knowledge in these matters can reply:

1) Try booting with the noapic argument (press 'e' to edit and add it to the list of kernel arguments in GRUB) and see if that will get you past the APIC stuff in recovery mode.

2) Try pressing Ctrl-C to cancel the disk check, then Ctrl-D to continue booting.

---

### Post by Atheil on 2008-04-16
> **wdaniels said:**
> The missing DSDT file should not be a problem - the kernel will just read the ACPI table from your hardware and the file is just a way to specify your own DSDT in case the one supplied by the OEM is buggy.  In any case this is for ACPI which has more to do with power management and similar functionality.  I don't see this having anything to do with your problem.

Unfortunately, I'm not much of an expert with such low-level problems, but I do have a couple of suggestions until someone with more knowledge in these matters can reply:

1) Try booting with the noapic argument (press 'e' to edit and add it to the list of kernel arguments in GRUB) and see if that will get you past the APIC stuff in recovery mode.

2) Try pressing Ctrl-C to cancel the disk check, then Ctrl-D to continue booting.

I'll try that 1st one, that might help, but I know the second one doesn't work. I can't kill the disk checker for some reason. I thought Ctrl-C would kill any process but I guess maybe the force check is protected . . .? Maybe there's some way to boot without having the computer force check?

---

### Post by Atheil on 2008-04-16
> **wdaniels said:**
> 1) Try booting with the noapic argument (press 'e' to edit and add it to the list of kernel arguments in GRUB) and see if that will get you past the APIC stuff in recovery mode.


Wow, that actually worked, sort of. The recovery boot worked, but it still force checked the HDD, but this time it worked. So I booted into the root user just fine. And when I restarted, the regular boot didn't call the force check. Thanks a lot for your help. I'm still worried that this didn't fix the actual problem, but just the symptoms, but being able to boot gets me a lot closer than I was before :P 

Btw, does anyone know what you can do when you've booted into recovery mode? I can't seem to access any of the folders I normally could under a regular boot, and I'm not sure how to shutdown properly from that screen, I usually just type exit, which kicks me off the command line, and then manually boot the computer.

---

### Post by wdaniels on 2008-04-17
The only times I've tried to use recovery mode, it's failed the same as the normal boot, so I'm not entirely sure what it does either :D  Probably it just starts a minimum of things, with safest options etc.

I agree you need to figure out properly the root cause of that problem - it always comes back to bite you if you don't.  It may be just a coincidence that it booted when you added the noapic argument - I'm sure I remember having a problem one time where fsck would fix a few things before hanging each time until eventually, after a few runs, it was all fixed and I could boot.

First thing I would do now is run fsck manually now to see if it turns up any remaining problems with the filesystem.  If not, then I guess you need to work out whether it just needed a few runs to get all the problems fixed or whether there is still some APIC related problem that causes the disk check to fail (I'm no expert but that seems unlikely).

I think you need to test booting again without noapic argument and see if it looks OK now.  Sometimes the log is misleading if whatever caused the crash hadn't been logged yet (i.e. the last message was for something that succeeded).  Perhaps look at the log on a successful recovery boot now and see if the disk check occurs after that APIC message normally?

Hope I'm making sense here :D

---

