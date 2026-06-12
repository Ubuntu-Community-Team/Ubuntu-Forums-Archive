---
title: "machine no longer wakes from sleep"
date: 2023-08-11
forum: General Help
---

### Post by koolmoedee on 2023-08-11
Wake from sleep was working fine on my ubuntu desktop until yesterday when I tried waking it and the CPU fan powered up, as usual, but the screen remained black even after several minutes.  Now it does this every single time I try to wake it from sleep and then I have to do a hard reset.  I installed a new wired mouse to my computer yesterday while it was in sleep mode and it has been this issue ever since, though I'm not sure if it is related.  Please advise.

Thank you.

---

### Post by MAFoElffen on 2023-08-11
Issues on "Waking from sleep" is usually from differing issues-- Kernel, graphics driver... 

You changed your mouse while being asleep? That might have caused a problem waking "that time", but would have recognized the change in hardware, and resolved itself after rebooting that time.

What output does this return?
```

grep -m1 'model name' /proc/cpuinfo
uname -r
grep . /sys/module/intel_idle/parameters/max_cstate
grep . /sys/class/backlight/acpi_video0/*

```
If you choose an older kernel from the Grub2 Boot Menu > Advanced Options, Does it work normally?

---

### Post by martinisaksson87 on 2023-08-15
[FONT=arial][SIZE=2][COLOR=#000000]I have the same problem. When trying to go to sleep it either is stuck on the splash screen, or have a black screen with the mouse visible. Everything is unresponsive. It also gets stuck when trying to power off the computer via the start menu or rebooting.
[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]I tried booting the system from an older kernel, &#8216;[/COLOR][COLOR=#000000]Ubuntu with Linux 5.19.0-1017-lowlatency&#8217; instead of &#8216;[/COLOR][COLOR=#000000]Ubuntu, with Linux 6.2.0-1009-lowlatency&#8217; and it seems to have fixed the issue for me.[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]
I couldn&#8217;t find the option to use an older kernel in the grub menu so I had to find out what kernel options I had from the terminal and then  change a line in the grub file. I followed [COLOR=#000000]these instructions[/COLOR] ([https://askubuntu.com/a/1393019)]("https://askubuntu.com/a/1393019") and had to change the line [/COLOR][/SIZE]
GRUB_DEFAULT=0 to, in my case GRUB_DEFAULT=&#8221;1>2&#8221; it might be different for you, depending on what option you have, just follow the instructions in the link.

Now, have this fixed my problem permanently or will it show up when upgrading to a newer kernel version again?
[/FONT]

---

