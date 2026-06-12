---
title: "Ubuntu doesn't shutdown if USB is used"
date: 2014-06-26
forum: General Help
---

### Post by shimoda on 2014-06-26
Hi!

I installed Ubuntu in an old machine (Pentium 4). I'm using gnome-fallback mode. All works very well, but when I try to shutdown the computer, it shutdowns system but instantly, it reboots again (the process last less than a second, in practical terms, is like a reboot).

After doing a lot of tests I discovered that the problem is with the USB. It has 2 USB, one with a printer and the other with a scanner. With all plugged, the computer reboots... If I unplug both, then Ubuntu shutdowns without problem!! If I unplug one of both, sometimes shutdown and sometimes not... :confused:

Really strange!! XD It seems that can be some problem with USB power...

I tried different acpi grub options, like "off", "force", power_nocheck... No one seems to change nothing... I thought it could be a Bios setting, but I changed ALL parameters regarding power management with same result... (The computer is dual booting with a Windows XP partition, and in XP it shutdowns without problem)

Any ideas? :rolleyes:

thanks!!! :)

---

### Post by tgalati4 on 2014-06-26
Install *acpitool* and post the output of:

```
acpitool -w
```

Try disabling the offending USB ports using the -W switch.

Boot into BIOS and uncheck the setting:  "Allow USB devices to Wake".

---

### Post by shimoda on 2014-06-27
this is the result with acpitool -w

```
 Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. PCI0	  S5	*disabled  no-bus:pci0000:00
  2. HUB0	  S5	*disabled  pci:0000:00:1e.0
  3. USB0	  S1	*enabled   pci:0000:00:1d.0
  4. USB1	  S1	*enabled   pci:0000:00:1d.1
  5. USB2	  S1	*enabled   pci:0000:00:1d.2
  6. USB3	  S1	*enabled   pci:0000:00:1d.7
  7. MODM	  S5	*disabled
  8. UAR1	  S5	*disabled  pnp:00:09
  9. UAR2	  S5	*disabled  pnp:00:0a
```

I tried to disable autowakeup with the -W option all 4 USB, but the computer restarts again... :?

And there's no option in Bios regarding USB and power management... Only WakeOnLan (and is disabled)

---

### Post by shimoda on 2014-06-27
Sorry, one more thing!

I discovered that it I unplug the scanner, and leave the printer connected but with power switched off, it shutdowns... Really seems something with the USB power...

---

### Post by tgalati4 on 2014-06-27
Are all of the devices plugged into the same power strip?  Do all of the devices have a proper grounding plug?  A small amount of power (a few volts) left on the USB bus could be a signal to boot the computer.  There could be damage on the motherboard--a blown diode.  Normally small, shutdown voltage is dissipated with diodes and resistors to prevent this kind of problem.  Because you leave the USB devices powered when you shut down the computer, there could be a voltage bias on the USB bus--enough to turn the computer on.  You could test this by hacking a USB key and adding a battery across the ground and 5VDC pins.  Try 1.5, 3, and 4.5 VDC and see if these small voltages will boot the computer through USB.

Otherwise, your work-around is to change your shutdown procedure, or just put the computer to sleep instead of shutting down.

Because of the age of a P4 system, this type of damage is common.  I have a couple of computers that I had to rewire to get them to boot because of blown power-on circuitry.

---

### Post by shimoda on 2014-07-02
> **tgalati4 said:**
> Are all of the devices plugged into the same power strip?  Do all of the devices have a proper grounding plug?  A small amount of power (a few volts) left on the USB bus could be a signal to boot the computer.  There could be damage on the motherboard--a blown diode.  Normally small, shutdown voltage is dissipated with diodes and resistors to prevent this kind of problem.  Because you leave the USB devices powered when you shut down the computer, there could be a voltage bias on the USB bus--enough to turn the computer on.  You could test this by hacking a USB key and adding a battery across the ground and 5VDC pins.  Try 1.5, 3, and 4.5 VDC and see if these small voltages will boot the computer through USB.

Otherwise, your work-around is to change your shutdown procedure, or just put the computer to sleep instead of shutting down.

Because of the age of a P4 system, this type of damage is common.  I have a couple of computers that I had to rewire to get them to boot because of blown power-on circuitry.

But if was only a physical problem, why it shutdowns well in Windows XP?
Can I do some kind of USB power management through Ubuntu to solve it?

thanks!!! :)

EDIT: I'll try the "sleep" approach

---

### Post by tgalati4 on 2014-07-02
Find an old copy of Ubuntu 10.04 on CD.  Boot from it and see if it shuts down normally.  What version are you currently running?  It could be a bug in the newer kernel that is not allowing a module to unload, and therefore not allowing a complete shutdown.  If it is not a hardware issue, then it's probably an issue of the new kernel running on on old hardware.

---

### Post by shimoda on 2014-07-03
I'm in 12.04... I did the contrary and updated to latest kernel...XD But the problem persists again...
Maybe I should do what you say and try and oldest version of Ubuntu...

---

### Post by tgalati4 on 2014-07-03
Did your computer work with 12.04.0 (the very first release of 12.04)?  Then did it stop working when you went to 12.04.4 (with a new kernel)?

---

### Post by shimoda on 2014-07-07
> **tgalati4 said:**
> Did your computer work with 12.04.0 (the very first release of 12.04)?  Then did it stop working when you went to 12.04.4 (with a new kernel)?

I don't know exactly what version I used but the computer didn't shutdown since first boot... I used and old Live CD with 12.04... Then I upgraded system and finally I also added a PPA with latest kernel... In all 3 cases the computer reboots instead of shut down... Do you thing that using newest version (14.04) will do something? 

I'll also try to boot a live CD with 10.04 and see what happens, but to have an old version of programs is not my preferred choice... hehe

thanks!!

---

