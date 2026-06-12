---
title: "Kernel woes on Hardy upgrade"
date: 2008-06-22
forum: General Help
---

### Post by jamespetts on 2008-06-22
I upgraded from Gusty to Hardy on my secondary computer, a VIA mini-ITX (EX1000G) a few weeks ago, but have had a rather odd problem that I did not have upgrading another computer in the house from Gusty to Hardy at the same time.

I cannot get the computer to boot in any of the new kernel versions that come with Hardy: whenever I boot, it will display the Ubuntu boot screen for about 5-10 minutes, with the progress bar bouncing backwards and forwards, rather than progressing, and I will then be dropped into a "BusyBox" shell. Whenever I reboot with an older kernel version, one from Gusty, it starts as normal and works fine (but, of course, I am then using an older kernel). 

I am wondering whether the problem is somehow connected to USB modules, since the whole thing seems to freeze shortly after USB initialisation, and I recall once seeing [FAILED] notices next to USB-related entries on startup logs/output, although, I must confess, I cannot now recall the details. I am using a USB keyboard and mouse.

Any assistance would be very much appreciated.

---

### Post by fahadsadah on 2008-06-22
Can you boot into recovery mode?
If so, drop into a root shell and type "aptitude reinstall linux-generic". (if you use a kernel other than generic, reinstall that one).

---

### Post by jamespetts on 2008-06-22
fahadsadah,

thank you for your reply :-) I tried restarting in recovery mode, but that went wrong, too. I got the following error:

```
[    43.989153] usbcore: registered new interface driver usbhid
[    43.989224] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:US

        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/ modules ls/dev
ALERT! /dev/disk/by-uuid/1c57fc6a-403e-4fec-9ac4-2b747433ed2 does not exist. Dropping to a shell!

BusyBox v.1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

Any clues?

---

