---
title: "UEFI Problem - ASUS G750 Dual-boot with Ubuntu 14.04 takes hours to boot"
date: 2014-06-13
forum: General Help
---

### Post by michael177 on 2014-06-13
[B][COLOR=#000000][FONT=Arial]I recently purchased an ASUS G750 with Windows 8 which I dual booted with Ubuntu 14.04. The computer has 2 drives, a 256GB SSD and a 1TB HDD. I put Ubuntu onto the SSD with my Windows installation. The dual boot worked great for several weeks, I would boot into GRUB and then be able to choose between Windows 8 or Ubuntu with both working fine. Recently the time it takes my computer to reach the grub screen has increased exponentially. A week ago it started taking a little longer than usual, then it became a frustrating 10 minutes, and now it takes my computer an exasperating 3 hours to reach the grub screen. Once I select an OS from the grub screen the computer boots completely normally into either Windows 8 or Ubuntu, both still work. Both operating systems work normally for the most part, but if I try to sleep or reboot, then the computer sits on a black screen for hours before it does anything again. One last issue is that about half the time when it boots the fans go wild, turning on and off over and over again until the computer is turned off again.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]So far I’ve used the boot-repair tool which created this if it will be of any help: [/FONT][/COLOR][COLOR=#1155CC]_[http://paste.ubuntu.com/7635146/](http://paste.ubuntu.com/7635146/)_[/COLOR]

[COLOR=#000000][FONT=Arial]I’ve also tried manually reinstalling grub, but nothing has helped at all. Again, the dual boot worked perfectly for a couple weeks and the problem isn’t really the booting, but rather the loading of grub. Any idea what the issue could be? Everytime I want to try a new fix it takes me hours upon hours waiting for the reboot so I’m really quite desperate.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
[/B]

---

### Post by oldfred on 2014-06-13
Usually boot issues are after grub. Before grub menu, you have UEFI loading and grub loading and that is all.
UEFI can be looking for other boot devices. Check that hard drive or Ubuntu is first in boot order. If others are first it may have to time out. Some have had network boot first and then without network boot takes forever.

Have you tried installing nVidia. Grub does try to use same video driver which could be an issue.
If you can boot you should be able to go into System settings.

 Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia or AMD... fglrx-upgrade

I do not think there are any log files before grub menu, so difficult to know what system is doing.

Have you set trim on for SSD? 14.04 does have a weekly trim but only enables for some systems. I have similar trim running daily with my 12.04. Have not checked my 14.04 install yet to see what it automatically did.

---

