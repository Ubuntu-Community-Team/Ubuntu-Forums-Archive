---
title: "Can't switch between operating systems"
date: 2012-10-29
forum: General Help
---

### Post by danfan100 on 2012-10-29
Hey I need some help, i just downloaded ubuntu onto my desktop which already had windows 7 on it. When i turn on the computer the screen where  you choose which operating system you want to you the moniter just says input signal out of range change setting to 144x900-60Hz . My brother wants to play his games on windows seven but I can't get it to switch over because of that message that pops up. I also downloaded this on my laptop and it works fine on there. Thank you for all help.

---

### Post by getThem_robots on 2012-10-29
Hi,

I believe you need to re-install grub (boot-loader and manager for Ubuntu which is recommended to be used for starting up Win7 for a dual boot computer).

This post should help you: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Look under "The Terminal Way" and follow instructions very carefully. Note that instead of looking for Ubuntu, you need to look for the device of your Win7 install.

-
Mahdi

---

### Post by AlexDudko on 2012-10-29
> **danfan100 said:**
> Hey I need some help, i just downloaded ubuntu onto my desktop which already had windows 7 on it. When i turn on the computer the screen where  you choose which operating system you want to you the moniter just says input signal out of range change setting to 144x900-60Hz . My brother wants to play his games on windows seven but I can't get it to switch over because of that message that pops up. I also downloaded this on my laptop and it works fine on there. Thank you for all help.

Can you provide us with the output of
> sudo fdisk -l

---

### Post by Mark Phelps on 2012-10-29
When you said you "downloaded it", that tells us nothing about HOW you installed it -- as a download is NOT an installation.

If you installed from a USB or CD/DVD, and installed Ubuntu into its own partition, then you installed GRUB by default as well.  In that case, GRUB might be using a default resolution that is not supported by your monitor.

When you boot the desktop, start pushing a SHIFT key until you get to a GRUB menu.  Once there, look for a recovery option. See if you can then boot into that.

Your laptop undoubtedly has very different hardware -- so just because it works on there means nothing about whether or not it will work on your desktop.

---

### Post by COMECON on 2012-10-29
Hi!
You could try booting from **Super Grub2 Disk**. Download the ISO [here]("http://www.supergrubdisk.org/super-grub2-disk/"). Burn it on a CD as you did with Ubuntu, and then boot from it. Select **Detect Any Operating System**, and try to boot from any of the detected operating systems, if they're shown.
If you can boot with it, I recommend you to boot with Ubuntu. Then just enter on a terminal (*Dash >> Terminal*) and write:
```
$ sudo grub-install /dev/sda
```
Assuming /dev/sda as your MBR. If you can do this, try to boot without the Supergrub disk.
I hope it works to us!

---

