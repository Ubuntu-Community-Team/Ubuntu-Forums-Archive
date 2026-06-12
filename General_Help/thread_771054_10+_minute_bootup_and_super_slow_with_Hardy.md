---
title: "10+ minute bootup and super slow with Hardy"
date: 2008-04-27
forum: General Help
---

### Post by akrapacs on 2008-04-27
Brand new Hardy install on my machine. It takes over 10 minutes to boot up. At boot, the splash screen progress indicator is abnormally slow at times and I get the same thing when I try to boot from any of the 8.04 live CDs (ubuntu, kubuntu, xubuntu) but NOT the 7.10 live cds.

After the boot finally completes, it can take between 30 - 60 seconds to load the file browser or the terminal window. Never had these problems with 7.10. There are no processes eating up the cpu, I have no idea why it's so sluggish.

Specs: P4 2.23 Ghz, 4GB RAM, ATI Radeon 9200

I have attached the dmesg output after a bootup. Anybody else have this problem? If I can't get this resolved I'm going to have to go with something else.

---

### Post by ghost_ryder35 on 2008-04-27
WOW.  I have never seen a boot take this long.  Are you running AMD 64bit

---

### Post by ghost_ryder35 on 2008-04-27
Looks like ACPI is the culprit.  Turn ACPI off by following these directions.  These directions are for a diffrent kernel so just look for the line that has your current kernel version.
 
[quote=magnes]
/boot/grub/menu.lst - there should be the file.
 
in the line looking something like that:
 
kernel /boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro noapic
 
you can add acpi=off
 
kernel /boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro acpi=off noapic
 
Hope it will work. I can't test it.
At system start you can type "e" (as edit) in the grub menu and then edit the lines of menu.lst entry to test (it won't be saved!).
[/quote]

---

### Post by ghost_ryder35 on 2008-04-27
so did it work?

---

### Post by akrapacs on 2008-04-27
No, unfortunately it still takes over 10 minutes to boot and it's still unusable once it boots. Perhaps I should check on some of the ACPI settings with motherboard. Thanks for the lead, I'll do some more investigation.

---

### Post by BattlePanic on 2008-04-30
I have a similar problem although not as extreme Since upgrading to Hardy I've found that booting is much slower.  From looking at the logs the problem seems to center around either detecting or initializing my disk drives.  I've described the issue in detail in [this post]("http://ubuntuforums.org/showthread.php?t=770284")

> **ghost_ryder35 said:**
> Looks like ACPI is the culprit.  Turn ACPI off...

After trying the acpi=off option Things boot much more quickly but I seem to lose some functionality.  Gnome's power meter no longer shows me how much battery life I have left on my laptop and I can't seem to connect to my wireless network.  From the little I've read, acpi has something to do with power management and computer configuration.  Power management and wireless networking are fairly important to me.  There must be a solution that doesn't involve turning acpi off but maybe this quick fix provides a hint as to what is slowing down the boot process so much.

Anyone have any further insight?

---

### Post by helpdeskdan on 2008-08-25
I still have the problem.  Funny, switching to a virtual terminal (ctl-alt-f1) seems to unfreeze it.

---

### Post by Camilia on 2008-10-28
How do I get the dmesg output?

---

