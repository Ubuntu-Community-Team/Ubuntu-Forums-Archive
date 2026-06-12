---
title: "Acer Aspire Out of Control"
date: 2013-09-25
forum: General Help
---

### Post by bak&#305;r on 2013-09-25
Dear all,

My Acer Aspire computer has acquired some unusual behaviors recently. I have two problems, which I suspect to be somehow inter-related:

[B]1. Screen brightness cannot be adjusted properly
[/B]The step size is too high. When I use Fn keys, there seems to be only 2-3 steps, whereas there are 5-6 steps when one uses the system settings GUI. I have experienced this problem every time after an upgrade, and used to be able to overcome the problem by changing a line to the following in /etc/default/grub:

```
[FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor" [/FONT]
```

However, it is useless this time. I have also tried adding acpi_osi=Linux additionally AND instead of acpi_backlight=vendor; but they are also useless.

[B]2. Fan runs at full speed all the time
[/B]This is happening for the first time. I have tried installing lm-sensors to check my CPU temperatures and the parameters are around 35-40 C, which I do not consider too high necessitating so much cooling.


I suspect that this problem is due to a recent update, but have no idea which. Any help will be appreciated.

---

### Post by Kirk Schnable on 2013-09-30
You're talking about screen backlight adjustments and fan speeds, both of which are likely ACPI related.

It looks like Ubuntu has struggled/is struggling with Acer ACPI support.

You may want to check your model here for any helpful notes:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer)

Here, you may find some (dated) workarounds for the backlight issues:
[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

You may want to have a glance at these, as well:
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/209837](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/209837)
[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

---

### Post by bak&#305;r on 2013-10-04
Thank you for your help, Kirk Schnable; I actually was not aware that there were machine specific archives like these. But unfortunately I could still not solve my problem. I tried boot command "nomodeset" from one of your links, but it only made things worse: the screen freezes. The fan problem has spontaneously disappeared after another update, just similar to how it started.

The exact model: Acer Aspie 5745G.

By the way, I am not a computer scientist.

---

