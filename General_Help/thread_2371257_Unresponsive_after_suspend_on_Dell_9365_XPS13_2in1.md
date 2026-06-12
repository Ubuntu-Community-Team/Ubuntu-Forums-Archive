---
title: "Unresponsive after suspend on Dell 9365 XPS13 2in1 - &quot;No hard drive detected&quot;"
date: 2017-09-12
forum: General Help
---

### Post by ninthdimension on 2017-09-12
I recently got the 9365 XPS13 2in1. Getting Ubuntu on there wasn't the easiest task (because the laptop was shipped in RAID mode instead of AHCI, and the Ubuntu installer couldn't see the hard drive). But now it's successfully dual booting Win10 and Ubuntu 16.04.2 I began to use it.

After closing the lid (sleeping), it's unable to resume. There's just a black, non-backlit screen, and none of the keyboard keys do anything. There's a light at the front of the laptop that flashes white and sometimes orange (I can't see any discernible pattern) and I find that I have to hold down ON/OFF several times before it comes back to life. However it doesn't resume to Ubuntu - instead it begins trying to boot from scratch, and runs the Dell pre-boot diagnostics which reports that "No hard drive is installed".

After quitting the diagnostics, it boots as usual into Win10 or Ubuntu.

I tried modifying /etc/grub/default as is suggested here:

[https://askubuntu.com/questions/875024/dell-xps-13-9365-2-in-1-wont-resume-after-suspend-ubuntu-16-04](https://askubuntu.com/questions/875024/dell-xps-13-9365-2-in-1-wont-resume-after-suspend-ubuntu-16-04)

[https://askubuntu.com/questions/771240/suspend-broken-on-ubuntu-16-04-lts-dell-xps-9350/778224](https://askubuntu.com/questions/771240/suspend-broken-on-ubuntu-16-04-lts-dell-xps-9350/778224)

[https://stackoverflow.com/questions/44527160/dell-xps-13-9365-2-in-1-hangs-on-suspend-ubuntu-16-04](https://stackoverflow.com/questions/44527160/dell-xps-13-9365-2-in-1-hangs-on-suspend-ubuntu-16-04)

but to no avail.

---

