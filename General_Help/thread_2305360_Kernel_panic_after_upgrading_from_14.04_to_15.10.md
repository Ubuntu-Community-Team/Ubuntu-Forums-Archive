---
title: "Kernel panic after upgrading from 14.04 to 15.10"
date: 2015-12-05
forum: General Help
---

### Post by tirengarfio2 on 2015-12-05
After upgrading from 14.04 to 15.10 Im getting a kernel panic, it says:
  > [INDENT]   Target filesystem doesn't have requested /sbin/init. /bin/sh: 0: Can't   open splash Kernel panic - not syncing: Attempted to kill init!   exitcode=0x00007f00 CPU: 0 PID: 1 Comm: sh not tainted   3.13.0-71-generic #114-Ubuntu Hardware name: EVGA International co. LTD E692 0.0/151-IB-E692, BIOS 4.6.5 02/05/2014.

 [/INDENT]
  I have tried all the kernel options that are shown in "Advanced  options for Ubuntu" (GRUB), but for all of them the error message is the  same.
  I just have 4 options at GRUB: Ubuntu, Advanced options, Memory test, Memory test.
  What should I do?

---

### Post by cariboo on 2015-12-05
Try Grub->Advanced options, and see if you can select an earlier kernel.

---

### Post by tammo-heeren on 2015-12-12
I have the exact same issue after updating from 14.04lts to 15.04. All grub advanced options, and choosing a different kernel result in the same issue. e2fsck -f was uneventful. Anybody have any suggestions in how to fix this?

---

### Post by pqwoerituytrueiwoq on 2015-12-13
based on the error i suspect
the issue was caused by the change away from upstart to systemd
i would guess that the grub boot line has changed, this can be fixed from a live cd/usb
to anyone reading this before this happens remove systemd and install upstart before rebooting to avoid this issue
i will now use a virtualbox to try to find a fix

---

### Post by pqwoerituytrueiwoq on 2015-12-13
after looking at a 15.10 install i think i know how to fix it
from your live CD open your installs [FONT=courier new]/boot/grub/grub.cfg[/FONT] file (eg [FONT=courier new]gedit /media/ubuntu/$SOMETHING/boot/grub/grub.cfg[/FONT]) you will probably want to do that as root

look for this
[URL="http://i.imgur.com/7fvSSKA.png"]
  [IMG]http://imgur.com/7fvSSKAt.png[/IMG]
[/URL]
change it to this
[URL="http://i.imgur.com/HugejWT.png"]
  [IMG]http://imgur.com/HugejWTt.png[/IMG]
[/URL]
then hopefully it will boot
once booted (if successful) run [FONT=courier new]update-grub[/FONT] and check your grub file for the change you made, if you don't see it
open your [FONT=courier new]/etc/default/grub[/FONT] file and change [FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" [/FONT]to [FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash init=/sbin/upstart"[/FONT]
then run [FONT=courier new]update-grub[/FONT] again then it will stay fixed

---

