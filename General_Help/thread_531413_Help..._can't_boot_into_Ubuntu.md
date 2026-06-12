---
title: "Help... can't boot into Ubuntu"
date: 2007-08-21
forum: General Help
---

### Post by montanj on 2007-08-21
After instilling ubuntu with wubi and rebooting i get the choice to boot with ubuntu which then fails with not finding a raid disk then the job won't start reloaded with wubi many times with the same error:confused:

---

### Post by mcklucker on 2007-08-28
Mine's doing the same exact thing.
Here's what it does:


Loading, please wait..
No RAID disks
        Check root=bootarg cat /proc/cmdline
        or missing modules devices: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
   /bin/sh: can't access tty; job control turned off
(initramfs) _

---

### Post by tuxcantfly on 2007-08-28
right after you select the Ubuntu entry on the menu, press ESC, that'll get you to a grub menu, there find the "Ubuntu (Original Kernel)" entry and press "e", that'll get you to another menu, find the "kernel ... " line and press "e", and at the end of the line, remove the "splash" and "quiet" options, press enter, then press b; it should give you more details

Also, go into Windows, and post the contents of the C:\wubi\logs directory (there should be 2 files in there)

---

### Post by 1oki on 2007-08-30
I had this problem a couple of times... Turns out the partition size was too small. What size are you trying to install it with? For me it did the "searching for RAID disk" thing if I was using less than 10 gigs... Anything 10 and above worked fine.

---

### Post by mark_lar on 2007-08-31
I know that this thread didn't have anything to do with me, but I followed those instructions and it now seems to be fine. I've got my fingers crossed!

*crosses fingers*

---

### Post by b2tharizzo on 2007-09-01
I'm having a similar problem. I installed wubi on my Windows Vista machine with 10 GB of allocated space for Ubuntu 7.04, and the install seems to go fine. However, when I reboot, it just hangs for awhile on a black screen and then loads into vista without the boot option menu. I recently upgraded my graphics card from an ATI Radeon 9800SE to an ATI X1650 Pro and also added 2 extra GB of RAM to my computer. It was after these upgrades that it wouldn't load into Ubuntu. I think the problem is that the computer's loading Windows Vista's winload.exe without loading the boot menu. Anyone know how to make it so it loads the boot menu instead of winload.exe?

---

### Post by tuxcantfly on 2007-09-02
> **b2tharizzo said:**
> I'm having a similar problem. I installed wubi on my Windows Vista machine with 10 GB of allocated space for Ubuntu 7.04, and the install seems to go fine. However, when I reboot, it just hangs for awhile on a black screen and then loads into vista without the boot option menu. I recently upgraded my graphics card from an ATI Radeon 9800SE to an ATI X1650 Pro and also added 2 extra GB of RAM to my computer. It was after these upgrades that it wouldn't load into Ubuntu. I think the problem is that the computer's loading Windows Vista's winload.exe without loading the boot menu. Anyone know how to make it so it loads the boot menu instead of winload.exe?

looks like vista overwrote the wubi bootloader, to restore it, do this:

1. go to C:\wubi\disks, and back all those files up to somewhere (home.virtual.disk and system.virtual.disk)

2. reinstall wubi, only before rebooting, take those backed-up disk images, and place them back to C:\wubi\disks

3. reboot, and you should be able to boot back into Ubuntu

---

### Post by b2tharizzo on 2007-09-03
I tried copying the files from the "disks" folder, but when I rebooted after reinstalling wubi, the screen just stayed black and wouldn't load into anything. Is there any way to make the windows vista bootloader show the option to boot into ubuntu?

---

