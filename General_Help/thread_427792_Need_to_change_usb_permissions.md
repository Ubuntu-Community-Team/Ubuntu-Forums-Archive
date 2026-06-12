---
title: "Need to change usb permissions"
date: 2007-04-29
forum: General Help
---

### Post by werewolf on 2007-04-29
I have a 2g thumb drive which, when plugged in, is mounted properly and I have r/w access.

The device node for it is /dev/sda1 which is verified by the listout of fdisk =l.  It's listed as having a Fat16 file system.  So in this respect, all is well with the world.

I am using Virtual Box to run WinXP Sp2, I have been able to create the filter for my thumbdrive in the USB section.

When I start the VM, my thumb drive is not recognized.  When I try to connect the device using the VM device menu, the tooltip over the device name says it is available, but it gives me an error saying that it failed to attach the USB device; it also states that I am not permitted to open the USB device, check USBFS permissions.

I have searched around a lot trying to find out how to do this, but I'm fairly wet behind the ears and don't totally understand how a thumb drive mounts or how to change permissions.

I have logged onto Konqueror as root, navigated to the mount point (?) /media/disk and have tried to change the permissions in from the context menu, but I am told I don't have sufficient access to do so.

I need to be able to connect to some kind of storage device outside the VM.

I would appreciate your help.  Please be specific when suggesting procedures as I am a newbie :O

Thanks,
David

---

### Post by werewolf on 2007-04-29
bump...

Alternately, how can I get my VM session to communicate with other storage devices on my box.  Seems as though the CD is read only :(

---

### Post by disturbedite on 2007-04-29
i've found for easier win compatibility to use fat32 for the filesystem.  i'd recommend reformatting it with the fat32 filesystem.

i don't know if that'll help with your issue, but its just an unrelated recommendation.

---

