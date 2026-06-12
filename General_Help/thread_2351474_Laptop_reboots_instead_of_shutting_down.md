---
title: "Laptop reboots instead of shutting down"
date: 2017-02-03
forum: General Help
---

### Post by marlon.aviz on 2017-02-03
**Specs:**
[LIST]
[*][SIZE=2]**OS**: *[COLOR=#333333][FONT=Ubuntu]Ubuntu 16.04.1 [/FONT][/COLOR]LTS Xenial amd64*[/SIZE]
[*][SIZE=2]**Laptop**: *Acer Aspire E 15 | Model E5-511-C7NE*[/SIZE]
[*][SIZE=2]**WakeOnLan**: Off[/SIZE]
[/LIST]

I looked on *stackexchange* and here on *Ubuntu* forum, but I couldn't solve it.

I try to shutdown my laptop, but instead it reboots after 3 or 4 seconds.

When I first installed the OS, it was fine. The problem started to happen after I *sudo **apt-get update && sudo apt-get upgrade*, but I already made a clean reinstall of the OS, so the problem is persisting through HD formatting.

I tried editing */etc/default/grub* to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi=force apm=power_off
and
GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq quiet splash"

```

And running *sudo update-grub* on both edits.

None of them worked, the computer actually gets stuck in a black screen with lots of lines of code (I waited a lot to make sure it was really crashed), so the line is back to its original:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

I tried shutting down through the GUI (top-left corner options) and the following commands:
[LIST]
[*]shutdown -P now
[*]shutdown -H now
[*]poweroff
[/LIST]

Doesn't work.

I also tried some other things I saw around the internet:
[LIST]
[*]Installing *laptop-mode-tools*.
[*]Turning WiFi adapter off (through the laptop keys, Fn+F3).
[*]Having something connected to the USB ports (I tried a USB flash drive).
[/LIST]

None of them worked.

---

### Post by marlon.aviz on 2017-02-05
I solved by changing from *16.04.1 LTS amd64* to *16.10 amd64*.

---

