---
title: "Standby/suspend Problem on 14.10"
date: 2015-03-28
forum: General Help
---

### Post by akindo2 on 2015-03-28
Hi guys and girls,

I am having problems with suspend (aka. standby) on the latest Ubuntu 14.10 running on a Gigabyte GA-D525TUD motherboard (Intel Atom D525 chipset). Ubuntu is installed on a USB stick, additionally there's 4 HDDs.

In the BIOS, when I set the ACPI standby to 

```
S1 (POS): Set suspend type to Power On Suspend under ACPI OS
```

and run pm-suspend, the machine spins down the harddisks and the power LED flashes, but it remains on (CPU, case and PSU fans are running). I can see it uses 30 watts (3 watts less than if it's running normally, but with the HDDs spundown).

When I set the ACPI standby to
```
S3 (STR): Set suspend type to Suspend to RAM under ACPI OS
```

and run pm-suspend, the machine powers completely down (probably it's going into hibernate mode). When I wake it up with a magic packet over the network, it powers on again, but it doesn't respond to ping. Also, if I wake it up with a mouse, the screen remains black.

What I would ideally like is for it to enter the kind of suspend mode we see on laptops, where it's using almost no power, but wakes up quickly. If this is not possible, the next best thing would be a hibernate mode, but where I can actually connect to it again after it's been woken up with a magic packet.

I'm aware it's difficult to debug these suspend issues, but does anyone have any tips?

Thanks a million!

---

