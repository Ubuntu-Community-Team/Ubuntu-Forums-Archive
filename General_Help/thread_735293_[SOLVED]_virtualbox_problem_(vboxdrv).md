---
title: "[SOLVED] virtualbox problem (vboxdrv)"
date: 2008-03-25
forum: General Help
---

### Post by robertchahine on 2008-03-25
i've installed virtualbox on my laptop, but i have the error about kernel or that /dev/vboxdrv was not created.
and the truth is that  /dev/vboxdrv was not created.
how can i create this file or fix it?
i tried to install virtual box from the terminal and the debian package, and installed the missing modules?
and i tried sudo /etc/...../start it gives me 

* Starting VirtualBox kernel module vboxdrv                                    FATAL: Error inserting vboxdrv (/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko): Invalid argument

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
root@houssam-laptop:/home/houssam# dmesg | tail
[ 5682.976000] [drm] Setting GART location based on new memory map
[ 5682.976000] [drm] Loading R300 Microcode
[ 5682.976000] [drm] writeback test succeeded in 1 usecs
[ 5797.212000] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 6117.632000] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 6923.312000] usb 2-2: USB disconnect, address 2
[ 7013.116000] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 7042.104000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 7042.104000] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[ 7042.104000] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.

---

### Post by pointone on 2008-03-25
Your answer is right there in plain sight: "Please disable the NMI watchdog by specifying 'nmi_watchdog=0' at kernel command line."

When Ubuntu is booting, hit "Esc" to enter the GRUB menu when prompted (this may not be required if you are booting more than one OS), then select the Ubuntu option, press "e", and a new submenu should appear. Select the "kernel" line and hit "e", then add "nmi_watchdog=0" to the end of the line and press enter. Press "b" to boot the system with the NMI watchdog temporarily disabled and try again.

If this works, you can permanently disable the NMI watchdog by editing "/boot/grub/menu.lst".

---

### Post by robertchahine on 2008-03-26
hey man, thank you so so much.
it works.
but how can i edit the "/boot/grub/menu.lst" to disable the NIMI watchdog for ever?

---

### Post by robertchahine on 2008-03-26
ah ok ok. i write this in the terminal:

```

gksudo gedit /boot/grub/menu.lst
```

and i add the nmi_watchdog=0 to the kernel line

---

