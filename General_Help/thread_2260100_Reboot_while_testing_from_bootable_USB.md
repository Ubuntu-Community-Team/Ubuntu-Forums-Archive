---
title: "Reboot while testing from bootable USB"
date: 2015-01-09
forum: General Help
---

### Post by plkoij on 2015-01-09
I'm testing 14.04 on a new laptop and want to test some changes that require rebooting. Is it possible to test these changes before actually installing the OS?

---

### Post by sudodus on 2015-01-09
Yes, but not with a standard live system. You need to make it a ***persistent*** live system with a casper-rw file or partition and the boot option persistent.

There are several links, see for example links from this tutorial page
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

and these links will help you do it automatically

[https://help.ubuntu.com/community/Installation/FromUSBStick#Install_and_run_Startup_Disk_Creator_alias_usb-creator](https://help.ubuntu.com/community/Installation/FromUSBStick#Install_and_run_Startup_Disk_Creator_alias_usb-creator)

'Stored in reserved extra space'

[http://zleap.net/unetbootln-usb-how_to/](http://zleap.net/unetbootln-usb-how_to/)

'Space used to preserve files across reboots'

Edit: But changes that involve the linux kernel will not work in persistent live systems. You can still test in a USB pendrive, but in such cases, make a full installation to a (second) pendrive, and test there before installing to the internal drive. An installed system will be very slow with a standard USB 2 pendrive. But it will be reasonably fast with a fast USB 3 pendrive even in a USB 2 port. See this link (post #6)

[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)

---

### Post by plkoij on 2015-01-09
I think I've already done this; I chose the option in Startup Disk Creator to store documents and settings in reserved extra space, and there is a casper-rw file on the USB. But if I create a file and then reboot it disappears. Why would this be happening?

---

### Post by sudodus on 2015-01-09
Did you add the boot option persistent (either in real time (when booting) in the grub menu, or edited into the boot configuration file).

See this link [One pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682")                 

***Edit*** the file **syslinux/txt.cfg** (in the FAT32 partition)

Add **persistent** like this:

from
```
append noprompt cdrom-detect/try-usb=true  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz  quiet splash --
```
to
```
append noprompt cdrom-detect/try-usb=true  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz  quiet splash persistent --
```

or if you want it ported to an installed system (if you are using the live system to install)

```
append noprompt cdrom-detect/try-usb=true  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz  quiet splash -- persistent
```

---

### Post by plkoij on 2015-01-09
Thanks! syslinux/txt.cfg already had the persistent option, but I had to add it to boot/grub/grub.cfg, and it works now.

---

### Post by sudodus on 2015-01-09
Good catch :-)

I see, you are booting from grub - I guess you are running in UEFI mode.

---

