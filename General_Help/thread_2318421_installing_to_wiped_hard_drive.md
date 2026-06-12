---
title: "installing to wiped hard drive"
date: 2016-03-25
forum: General Help
---

### Post by JamButty on 2016-03-25
After trying to save my laptop after many attempts, I abandoned it,  bought a new computer, then came back to that laptop drive, wiped it clean, thinking reinstallation of Ubuntu would be a snap. It ain't. it is standard BIOS (not UEFI), but I remember reading something about needing to write the installation to block zero, which seems impossible without specialized software. Created a partition as close to block zero as possible, but no go. So - is there any shortcut for installing Ubuntu to an entirely wiped hard drive?

---

### Post by Bucky Ball on 2016-03-25
Boot from the install media, 'try ubuntu', when at a desktop launch Gparted.

Locate that drive. Wipe partitions if there are any on there then, from the options along the top, 'Create partition table' from the 'Device' (I think) menu. Then create partitions or click the icon on the desktop and try the install.

---

### Post by sudodus on 2016-03-26
Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Please boot into the install DVD/USB drive and run the following commands in a terminal window

```
df
sudo parted -ls
sudo lsblk -fm
```

and post the output in a reply.

Knowing these things about your computer makes it easier to help you.

---

### Post by JamButty on 2016-03-26
Sorry, I left out some critical points:  the bios is locked (original owner put a password on it, but had no memory of that) so not possible to change boot menu to boot from thumbdrive or external CD drive. Internal cd drive is shot. I did wipe all partitions (with HD plugged into another computer) and created a new one via Gparted as close to block 0 as it allowed and put installation media there, hoping the default boot to HD would invoke it. It did not. So I cannot boot into the install DVD/thumbdrive on that system to issue those commands. It is an HP Elitebook 8530p, according to CNET is: Intel Core 2 Duo T9400 / 2.53 GHz  memory: 8 GB ,DDR2 SDRAM  ATI Mobility Radeon HD 3650 - 256 MB  802.11a/b/g/n (draft), Bluetooth 2.0 EDR, Intel WiFi Link 5300  ------------- So I am asking if it is possible, through standard write operations to the hard drive, to create media on an empty partition on HD that would allow a boot into that partition and invoke the installation.

---

### Post by sudodus on 2016-03-26
I suggest that you move the internal drive into another computer and install Ubuntu into it. Avoid proprietary drivers, install only a basic system with free linux drivers into the drive.

Then move the drive back to this HP Elitebook 8530p and try booting. Maybe you need some boot options, for example ***nomodeset*** until you install a proprietary driver for the Radeon graphics. Maybe it works well directly with the free driver.

-o-

If you have problems to connect the drive internally, maybe you can connect it via

- eSATA or
- USB via a 'USB to SATA cable' (actually an adapter) or external box.

-o-

Try to figure out if the computer is running in UEFI or BIOS mode. If you can figure it out - install in one of the modes, and if it does not work, try in the other mode.

An alternative is to start with a live-only system, that can boot in both UEFI and BIOS mode. A system installed by cloning from an Ubuntu desktop amd64 system should work. You can install it with mkusb into an internal hard disk drive too: 'Toggle USB-only' in an mkusb menu.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

When the computer has booted from this system, you can investigate the boot mode and get it right for the installed system.

```
test -d /sys/firmware/efi && echo efi || echo bios
```

---

### Post by Bucky Ball on 2016-03-26
I don't know how au fait you are with tinkering with hardware, but if you download your laptop's manual and locate where the cmos battery is and pop it out for a couple of minutes then put it back in, that will clear the BIOS, reset it. Including wiping the password. :)

* Scratch that. I've just been looking for where it is and can't find anything about it. One of the HP experts on the web site does say there's no way of retrieving a password or resetting it unless you have:

1/ answered the three secret questions you're given when setting the password, or
2/ registered it with HP

You could ask whoever owned the laptop whether they did either of these. Even following sudodus' suggestion, which is a good one and seems your only option for now, you are going to want to get to the BIOS one of these days. :|

---

### Post by JamButty on 2016-03-31
Thanks BuckyBall, but the original owner claims never to have set the password and knows nothing about it.  HP is of course willing to reset the BIOS for a fee greatly exceeding the value of the laptop. Been all through those options.

Sododus - need to study your suggestions a bit - not sure I understand them right now. In the interim my current machine, a desktop, suddenly cannot login to the Ubuntu system (writing this from windoze partition) so I'll be trying to fix that first.


thanks!

---

