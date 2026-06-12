---
title: "Error screen appears after grub menu, not booting"
date: 2024-07-23
forum: General Help
---

### Post by immattao on 2024-07-23
Hi! I need help with solving an issue that's causing my laptop to not boot to Ubuntu. I am new to Linux in general and Ubuntu in particular.


**My setup**: Dual boot Ubuntu 24.04 and Windows 11 on ASUS Zenbook 14x.


**The issue**: I was trying to make bluetooth pairing work more smoothly between the two OS, following [this guide on Github]("https://gist.github.com/madkoding/f3cfd3742546d5c99131fd19ca267fd4"). At one step, I got stuck since I couldn't access the registry key for the bluetooth device. I tried a few things to get access, as suggested in [this post on the Microsoft help forum]("https://learn.microsoft.com/en-us/answers/questions/1340219/access-denied-when-change-regedit-value"). After that, when I boot into Ubuntu, after the grub menu, I was met with the screen in the picture. 
[IMG]https://i.redd.it/tt7rwhbjd3ed1.jpeg[/IMG]
So a bunch of log messages, for eg.
[FONT=courier new][  OK  ] Started cups.service - CUPS Scheduler[/FONT]

And a few blue error messages, for eg.
[FONT=courier new]iwlwifi 0000:00:14.3: WRT: Invalid buffer destination[/FONT] 


The last line is an error message that is grey and not blue, it says:
[FONT=courier new][     7.285379] ucsi_acpi USBC000:00: error -ETIMEDOUT: PPM init failed[/FONT]

And the screen just stays there indefinitely.

[B]
What I tried[/B]: I tried press e to edit boot options at grub, append [FONT=courier new]modeset=0[/FONT] after [FONT=courier new]splash[/FONT] and then press F10 to boot. This did not fix the issue. I also tried Ctrl-Alt-F2 to get to TTY, login and ran [FONT=courier new]sudo apt upgrade[/FONT]. This did not help either.


Please let me know what you think I should try! Thanks a bunch &#128513;

---

