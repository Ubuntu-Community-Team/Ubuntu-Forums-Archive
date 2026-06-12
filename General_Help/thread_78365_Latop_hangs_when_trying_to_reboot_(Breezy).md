---
title: "Latop hangs when trying to reboot (Breezy)"
date: 2005-10-18
forum: General Help
---

### Post by wired on 2005-10-18
Hi All,

i have a strange problem with Breezy, on my Satellite A20. For some reason, when I try to reboot my computer, it get's to the point where is says "umount :tmpfs busy" and it just hangs like that, not doing anything. I never had that problem in Hoary, so it's a Breezy issue. Can anyone help please? Thanks.

P.S I did not play around with mtab or fstab, so the problem is from the fresh installation.

---

### Post by tez218 on 2005-10-20
I too have the same problem with my Toshiba Satellite A45-S120. When trying to reboot with 5.10, the system always hangs. Never happened with 5.04 or any other distro ive used. This is still on a fresh install also, not and upgrade from 5.04.

---

### Post by chubuntu on 2005-10-23
I have a sony Vaio VGN-S380P.  Was running hoary A-OK, and just did a dist-upgrade to breezy today.  Everything from hoary nice (sound, Wifi/WPA supplicant, bluetooth, etc), but having strange reboot hanging problem.  I'm running official nvidia 7667 drivers for 6200 go with no problem after installing new kernel source + headers and recompiling.

From gnome, If I do a System > Logout > Shut Down, works fine.
From gnome, do a System > Logout > Restart the computer, hangs at:
* Shutting down LVM Volume Groups..... [ok]
* Rebooting

From command line, shutdown -h now
switches to text logon tty1
then powers down nicely.

From command line, shutdown -r now
switches to text logon tty1
then I see some scrolling gibberish repeat on the screen, hung.

From command line, reboot
screen just goes blank, then nothing - hangs.

Wondering where to start to debug this?  Sure, I can just shutdown then re-power but would like to fix it.  Log files to look at?  Maybe something with APM or ACPI?  Thanks.

---

### Post by wired on 2005-10-26
After days spent on trying to fix this, I discovered that kernel 2.6.12.9 presents the actual problem, so by compiling newer version of kernel, I've managed to solve this issue. Hope this works for you guys.

---

