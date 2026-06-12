---
title: "System Randomly Crashes and Hangs"
date: 2023-11-19
forum: General Help
---

### Post by felix920506 on 2023-11-19
Hi, I have a dedicated machine running a Jellyfin Server on Ubuntu server 23.04. The system has been randomly crashing since it was installed in May and I couldn't figure out what the cause was.

System Specs:
Intel Core i5-9400F
ASUS B360-F
8GB DDR4 RAM
2x WD Green 120GB SSD (One for OS one for Jellyfin temp files)
Intel Arc A750 Graphics Card

System behavior:
It would run for a while (ranging from a few hours to a few months), then the whole system would crash. No kernel panic screens, no kernel dump reports, no nothing. The screen would go black and the whole system would remain in that state until it got manually and forcefully restarted. It would then boot up normally without issues, the cycle repeats. Everytime the system crashed it was doing nothing. While the system isn't on a UPS, other systems around it aren't having the same behavior.

Troubleshooting Steps taken so far (All of which didn't solve the problem):
Enable Kdump (never dumped anything when one of these crashes happened)
Run Memtest on the memory (No errors)
Run fsck on boot drive (No errors)
Change the Power Supply
Change the MB, CPU and RAM

---

### Post by MAFoElffen on 2023-11-20
I see an Intel ARC 750... You said Server Edition right? You didn't load a Desktop on it right?

Could you please run the 'system-info' script in my signature line and post the URL to the report it generates.

Do you have "consoleblank=0" in line GRUB_CMDLINE_LINUX_DEFAULT= line in /etc/default/grub?

---

### Post by zgurt on 2023-11-20
Hello !

I've been experiencing EXACTLY the same issues and I also run a Jellyfin Server on Ubuntu Server LTS.

Here are my specs :

Ryzen 7 1700
MSI B450M PRO MAX II
16B DDR4 RAM
4x HDD FIRECUDA 4TB in ZFS RAID-Z1
1x SSD 970 PRO for L2 cache and OS
GTX 1660 Super
LC-POWER LC550 80+ Platinum

Exactly the same behavior as felix mentionned.
Absolutely nothing in logs.

I ran your script but doesn't want to post it since it has several personnal infos.

I don't have "consoleblank=0" in line GRUB_CMDLINE_LINUX_DEFAULT= line in /etc/default/grub
I have GRUB_CMDLINE_LINUX_DEFAULT=""

Also tried memtest 86+ (passed without errors)

Thank you very much for helping us !

---

### Post by felix920506 on 2023-11-20
> **MAFoElffen said:**
> I see an Intel ARC 750... You said Server Edition right? You didn't load a Desktop on it right?

Could you please run the 'system-info' script in my signature line and post the URL to the report it generates.

Do you have "consoleblank=0" in line GRUB_CMDLINE_LINUX_DEFAULT= line in /etc/default/grub?

> I see an Intel ARC 750... You said Server Edition right? You didn't load a Desktop on it right?
Yes. I did not load a desktop on this machine.

> Could you please run the 'system-info' script in my signature line and post the URL to the report it generates.
This is its output.
[https://paste.ubuntu.com/p/Hnkc5HGzV9/](https://paste.ubuntu.com/p/Hnkc5HGzV9/)

> Do you have "consoleblank=0" in line GRUB_CMDLINE_LINUX_DEFAULT= line in /etc/default/grub?
No, I do not have this line in /etc/default/grub

---

