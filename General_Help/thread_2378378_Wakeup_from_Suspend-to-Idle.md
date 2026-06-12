---
title: "Wakeup from Suspend-to-Idle"
date: 2017-11-22
forum: General Help
---

### Post by togop2 on 2017-11-22
I'm trying to use Suspend-to-Idle, also known as "freeze" state with my laptop (Surface Book), and, for the most part, it works. However, I have problems with getting my laptop to wake up.

In the Linux documentation, I see:
> The system is woken up from this state by in-band interrupts, so theoretically any devices that can cause interrupts to be generated in the working state can also be set up as wakeup devices for S2Idle.

I'm trying to setup the power button to act as a wakeup device, but a specific key on the keyboard would work as well. I have the following problems:
1) The power button is not present in /proc/acpi/wakeup and doesn't have a /sys/.../power/wakeup file in its /sys node. It IS DETECTED by the system, I can use it to trigger the suspend (or whatever other action I assign to it), but I can't set it up to wakeup my device.
2) I could set the keyboard as a whole to wakeup the laptop. However, it comes with a touchpad which is very sensitive and wakes up the laptop immediately. I can't seem to set the wakeup only on key presses, but disable it for the touchpad - they seem to go together.

Since I'm using a purely software suspend, I think it should be possible to make my system wakeup on a specific key or power button, even if those don't work with ACPI. Any ideas how I can approach that?

---

