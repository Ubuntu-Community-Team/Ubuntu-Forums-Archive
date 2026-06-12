---
title: "Desktop won't wake after suspend"
date: 2016-01-12
forum: General Help
---

### Post by corsam on 2016-01-12
I'm using a fresh installation of 14.04. The power settings are set so the computer doesn't suspend after a period of inactivity. I'm also using caffeine to disable the screensaver. The computer still suspends after 10 to 15 minutes of inactivity, and I can't wake it. The Num Lock light on the keyboard goes off, but the laser from the mouse remains on. It's a custom computer, I think it has an Asus Motherboard (I didn't build it myself, but I can check if necessary). Here's some other information requested on a similar thread:

> [COLOR=#000000]The contents of your /var/log/pm-suspend.log file[/COLOR]

This file doesn't exist. I have:

[LIST]
[*]/var/log/pm-powersave.log     [http://paste.ubuntu.com/14480131/](http://paste.ubuntu.com/14480131/)
[*]/var/log/pm-powersave.log.1  [http://paste.ubuntu.com/14480132/](http://paste.ubuntu.com/14480132/)
[/LIST]
> Information about your video card. sudo lspci -vnn | grep -A12 VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8534]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915


00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)

>  your current kernel command line: cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.19.0-25-generic root=UUID=f49201f2-56c6-417a-b287-a0d38236c40e ro quiet splash vt.handoff=7


Thanks!

---

### Post by Seanan on 2016-01-12
You don't need caffeine to disable the screensaver and it may be conflicting.
Can you soft reboot and get to a command line? If you can try this:
Uninstall caffeine then use these commands 

[COLOR=#111111][FONT=Ubuntu]To disable the screen blackout:
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]gsettings set org.gnome.desktop.session idle-delay <seconds> (0 to disable)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]To disable the screen lock:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]gsettings set org.gnome.desktop.screensaver lock-enabled false[/FONT][/COLOR]

---

### Post by corsam on 2016-01-13
Okay, I gave that a try. Thanks.

---

### Post by corsam on 2016-01-13
The issue happened again after I made the changes you recommended. It seemed like I had been inactive for less than 10 minutes. Are there any other settings I can check?

---

### Post by Seanan on 2016-01-22
Thats strange. I am sorry that I can't help you much. Maybe there is something wrong with the script?

---

