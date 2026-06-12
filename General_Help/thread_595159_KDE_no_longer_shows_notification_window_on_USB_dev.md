---
title: "KDE no longer shows notification window on USB device"
date: 2007-10-28
forum: General Help
---

### Post by kung fu buntu on 2007-10-28
I don't know what has happened but it stopped working...
I formatted the thing in gparted... But to check it wasn't that I tried another USB flash drive... and nothing... no notification window.

I checked kcontrol but it's all the same. I even tried setting it to always open a notification window (instead of asking), but nothing.

**sfdisk -l** shows the device and I can mount it as well. But I would like to be able to mount it automatically with KDE instead of havving to go to the command line every time :mad:

thanks!

---

### Post by Caffeine_Junky on 2007-10-29
So, if you plug the flash-drive in then go to "System Menu" > "Storage Media" is the device showing as mounted in there? ..if not, try: View > "Show hidden files",  ...this has worked for me before...

You say that Notifications were working, and you have not changed anything in the settings,  maybe try toggling the settings and "Apply" them again and reboot...  also, check your package manager and make sure all the things you need are still installed, like "pmount"

In kcontrol > Desktop > Behavior > Device icons, enable "show device icons" and see if when your usb device is pluged-in/mounted an icon shows up on the desktop.

I agree with you that nothing should have changed if you did not change it, but now it is just a matter of getting  that device to auto-mount  again.   As for the Notification window that pop's up on connecting the device, I have been sitting here trying to Disable mine so I can trouble-shoot your problem, and I can not even find a setting for it lol  

good luck

ps: I  have had this "notification and mounting" issue in Kubuntu, but Sidux dose not seem to have this problem (yet) ... :-k

---

### Post by kung fu buntu on 2007-10-29
when plugged, the device doesn't show on "System Menu" > "Storage Media"

I tried toggling settings, although I didn't reboot.

I have pmount and will upgrade it. Do I need autofs? Anything else?

About disabling the "notification window" try:
kcontrol / peripherals / storage media ; select unmounted removable media; select "do nothing" and click on "toggle as auto action"

---

### Post by nowshining on 2007-10-29
u must be having trouble with HAL I am guessing, does it give any error when opening up removable drives and media?

---

### Post by Caffeine_Junky on 2007-10-29
> I have pmount and will upgrade it. Do I need autofs? Anything else?

No, pmount is all you will need

> About disabling the "notification window" try:
kcontrol / peripherals / storage media ; select unmounted removable media; select "do nothing" and click on "toggle as auto action

Thanks for the instructions, I will check that out...

---

### Post by kung fu buntu on 2007-10-29
> **nowshining said:**
> u must be having trouble with HAL I am guessing, does it give any error when opening up removable drives and media?I also tried restarting that crazy AI system but no change.
I also rebooted the system and still no change. If I insert a DVD I get a notification window. So it's not making much sense :? Besides that, I tried plugging the USB stick as another user and surprise: *no* notification window :mad:
It gets me to suspect it's a system problem but it only affects (USB) removable medium devices.

oh and BTW, KDE is so full of bugs... Now I can't un-toggle the "open new window" (which doesn't work) for "unmounted removable medium"

Here is my dmesg from plugging and unplugging the usb flash drive:```
usb 7-2: new high speed USB device using ehci_hcd and address 4
usb 7-2: configuration #1 chosen from 1 choice
scsi7 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 7:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS
SCSI device sdc: 4062208 512-byte hdwr sectors (2080 MB)
sdc: Write Protect is off
sdc: Mode Sense: 43 00 00 00
sdc: assuming drive cache: write through
SCSI device sdc: 4062208 512-byte hdwr sectors (2080 MB)
sdc: Write Protect is off
sdc: Mode Sense: 43 00 00 00
sdc: assuming drive cache: write through
 sdc: sdc1
sd 7:0:0:0: Attached scsi removable disk sdc
sd 7:0:0:0: Attached scsi generic sg3 type 0
usb 7-2: USB disconnect, address 4
```

linux gets me so :mad::mad::mad:
windows come back :lolflag:

---

### Post by kung fu buntu on 2007-10-30
Upgraded KDE and HAL. Rebooted.

Things started working. I did end up facing another bug: I couldn't untoggle the auto action :mad:
But I found a workaround [here]("https://forums.gentoo.org/viewtopic-t-430804-highlight-.html"): kwrite ~/.kde/share/config/medianotifierrc &
The bug was closed, then opened and now a patch was submitted [kde notification bug]("https://bugs.kde.org/show_bug.cgi?id=131734")

Things are now working smoothly \\:D/\\:D/\\:D/
The question is... for how long?! :lol:

---

