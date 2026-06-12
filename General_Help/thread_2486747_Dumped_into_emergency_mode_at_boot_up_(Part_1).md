---
title: "Dumped into emergency mode at boot up (Part 1)"
date: 2023-05-09
forum: General Help
---

### Post by stuarte83 on 2023-05-09
Hi,

Currently I am unable to log into Kubuntu 22.04.2 on my Toshiba SATELLITE L870-18V laptop. (This second hand laptop has worked well with Kubuntu's 20.04 LTS, and 22.04 LTS up to kernel 5.0.15-70. Instead I am dumped into emergency mode with the screen showing the following text.

You are in emergency mode. After logging in, type "journalctl -xb" to view
system logs, "systemctl reboot" to reboot, "systemctl default" or "exit"
to boot into default mode.
Press Enter for maintenance
(or press Control-D to continue):

I then press Enter followed by "journalctl -xb". Single stepping through the log I find the following (amongst several "errors").

platform eisa.0: Cannot allocate resource for EISA slot 2
platform eisa.0: Cannot allocate resource for EISA slot 3

Given that the hardware is a laptop, can I take it that these can be ignored ?

Stuart

---

### Post by oldfred on 2023-05-09
Are you able to get grub menu? & boot to recovery mode?
Or no grub menu? Even if using shift key (BIOS) or escape key (UEFI)?

If grub booting issue, this can help. But if only grub & it is auto booting and then you have issue this may only tell us it is not grub.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by stuarte83 on 2023-05-10
Hi oldfred,

Thank you for your swift reply.
 
The laptop is set up to use csm (legacy) bios booting. Yes, I can get to a grub menu using "shift" at boot up.

Where do I find the BootInfo summary report ?

Stuart

---

### Post by tea for one on 2023-05-10
> **stuarte83 said:**
> Yes, I can get to a grub menu using "shift" at boot up.
Can you boot successfully into an earlier kernel?
> **stuarte83 said:**
> Where do I find the BootInfo summary report ?
You have to download the boot-repair utility in a live "Try Ubuntu" session if your PC does not boot.
2nd option in this link has instructions [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by stuarte83 on 2023-05-16
Good morning all,

I have come to the conclusion that the problem was somehow caused by the little MiFi that I use to connect to the internet. This was acquired in 2020 along with an HP Chromebook. The MiFi has worked flawlessly since that time with both the Chromebook and the laptop. It still works flawlessly with the Chromebook.

However, it started giving usb read/64 error -32 and more recently read/64 error -71 solely with the laptop. This started when I was using Kubuntu 22.04.1. I believe the problem started with its later kernels, definitely kernels 5.15.0-70-generic and 5.15.0-71-generic, although I think(!) the usb errors started with at least one kernel version before that, but I am not sure.

My current workaround is to boot the laptop and then(!) connect the MiFi. By following this process, the usb errors do not appear and I can still access the internet.

So, my thanks to all who have responded to my call for help. It is very much appreciated.

Stuart

---

