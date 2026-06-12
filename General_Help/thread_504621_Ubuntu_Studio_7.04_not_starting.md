---
title: "Ubuntu Studio 7.04 not starting"
date: 2007-07-19
forum: General Help
---

### Post by saximus on 2007-07-19
Hello,

I know that these issues may be difficult to fix, but I'm hoping that someone is familiar with the problem and that it is an easy fix.. All right - here we go.

I just installed Ubuntu Studio 7.04 on a 15gb partition today and the installation finished without any problems.

When the computer restarted after finishing the installation, it automatically started Ubuntu, went through the first screen with the loading bar and went on to start normally. But something unusual happened. I can't remember exactly, but I was told that some files had not been checked in a certain amount of days (a LOT of days as far as I remember 14000 or something..) - the system started to check the files, and a progress bar came up. Immediately after the progress bar finished, something came up as [FAILED], but I don't know what that was unfortunately. Nothing else had come up as failed or started before it though.

I have now reinstalled everything, but I can't even get past the ubuntu loading screen now. I get the following error message if I try starting Ubuntu, kernel 2.6.20-15-lowlatency after waiting for quite a while for it to load with no progress at the progress bar:

-----------------------------------------------------------------------------------------------------------------------
BusyBox v.1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh: can't access tty; job control turned off
(initramfs)
-----------------------------------------------------------------------------------------------------------------------

If I try starting Ubuntu, kernel 2.6.20-15-generic I get the following messages:
-----------------------------------------------------------------------------------------------------------------------
Starting up...
Loading, please wait...
[2.620568] irq 18: nobody cared (try booting with the "irqpoll" option)
[2.620687] handles
[2.620720] [<f887ff10>] (usb_hcd_irq+0x0/0x60) [usbcore]
[2.620832] Disabling IRQ #18
[33.488448] ata3.00: failed to set xfermode (err_mask=0x40)
[68.581428] ata3.00: failed to set xfermode (err_mask=0x40)
[103.674404] ata3.00: failed to set xfermode (err_mask=0x40)

Check root = bootarg cat/proc/cmdline or missing modules, devices: cat/proc/modules/ls/dev

ALERT! /dev/disk/by-uuid/de7ae1ff-5ea0-4e0f-ac95-039851411383 does not exist. Dropping to shell!

BusyBox v.1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh: can't access tty; job control turned off
(initramfs)
-----------------------------------------------------------------------------------------------------------------------

To me it looks like I might have to skip installing Ubuntu Studio on this computer, but if someone is able to show me how to fix this easily; I would appreciate it. I am not steady in linux though, so if this is very difficult; it might be an idea to skip it. I would really like to get this onto my system though, because I want to learn more about linux. 

Hope that someone can help! 

- saximus

---

### Post by saximus on 2007-07-19
btw - if my hardware might be an issue; I've got a CPUID file with all details that I can post here. Tell me if it is needed:)

---

### Post by saximus on 2007-07-22
No-one's seen this problem before, or what?

---

### Post by fredj on 2007-07-22
From time to time Ubuntu will check your disk drives at boot up time. It looks as though the test failed with
errors on your system. The command to run a disk check is fsck. If you open a terminal and type
'man fsck' you will get a list of the options for fsck. I suggest you run a test again yourself and note any error
messages carefully. Also check your free disk space to make sure that you have some.

---

### Post by saximus on 2007-07-23
I tried checking the system as you said:

root@saximus:/home/saximus# fsck
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda7 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda7: recovering journal
/dev/sda7: clean, 151293/1818624 files, 865513/3636706 blocks

It seems to tell me that the system is fine, but it didn't spend any time checking the system and although fsck tells me everything is fine - the problem is still there..

---

### Post by saximus on 2007-07-23
There seems to be a problem with irq 18 from all I can understand..

I've tried accessing my BIOS to change the settings for irq 18, but my BIOS shows only up to irq 15 - could this be a problem? Does anyone know exactly what irq 18 refers to?

---

