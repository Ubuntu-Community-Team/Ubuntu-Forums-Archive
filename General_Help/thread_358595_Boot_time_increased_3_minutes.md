---
title: "Boot time increased 3 minutes"
date: 2007-02-11
forum: General Help
---

### Post by ibejohn on 2007-02-11
Just a few minutes ago, my boot times suddenly went from 53 seconds to a login prompt, up to 231 seconds.  I'm running a LAMP server (console only) that is up-to-date as of today, and am not sure what I might have done to increase the boot time.

The last package I installed was ifenslave-2.6 in an attempt to see if I could bond my two NIC's.  I followed the instructions at [http://www.debianadmin.com/linux-ethernet-bonding-configuration.html](http://www.debianadmin.com/linux-ethernet-bonding-configuration.html), and it seemed to work, but somewhere along the way my machine locked up and I had to do a hard reboot.  After that, my boot time increased.  I removed the bonding changes and restored my interfaces file back to just a single device but the long boot time remains.

I enabled verbose output in GRUB and see it is delaying while "* Starting kernel event manager" just before it (apparently) loads the lp0 driver.  I tried disabling my parallel port and sound (AC97) in my BIOS but it didn't help the boot time; it just skipped loading those drivers.

Can anyone help me figure out what it's doing in those 3 minutes and/or tell me how I can get my shorter boot times back?  If I hit CTRL-ALT-DEL on the console keyboard during this wait, it does kill what it is running (rcS and rc6 are listed as killed on the console) and give me a login, but I'm still not sure how to tell what it was doing.

Thanks,
  John
  
Here is an /var/log/messages excerpt from earlier in the day:

```
[FONT="Courier New"][   34.301562] EXT3-fs: mounted filesystem with ordered data mode.
[   40.540897] FDC 0 is a post-1991 82077
[   40.769857] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.786501] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.937014] parport: PnPBIOS parport detected.
[   40.937066] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.962784] input: PC Speaker as /class/input/input1
[   41.128284] Linux Tulip driver version 1.1.14 (May 6, 2006)
[   41.128769] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   41.128774] GSI 20 sharing vector 0xE9 and IRQ 20
[   41.128780] ACPI: PCI Interrupt 0000:03:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 233
[   41.129399] tulip0:  MII transceiver #1 config 1000 status 7849 advertising 01e1.
[   41.135736] eth1: ADMtek Comet rev 17 at Port 0xac00, 00:03:6D:16:C2:42, IRQ 233.
[   42.282839] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[   42.282843] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 23 (level, low) -> IRQ 201
[   42.607770] intel8x0_measure_ac97_clock: measured 58822 usecs
[B][   42.607773] intel8x0: clocking to 47057
[   43.154083] lp0: using parport0 (interrupt-driven).[/B]
[   43.312509] it87: Found IT8712F chip at 0x290, revision 7
[   43.609429] Adding 570268k swap on /dev/disk/by-uuid/e918f20d-c70b-40b7-82f3-461714f7e23d.  Priority:-1 extents:1 across:570268k
[   43.759090] EXT3 FS on hda1, internal journal
[   44.035775] kjournald starting.  Commit interval 5 seconds
[   44.050835] EXT3 FS on hdc1, internal journal
[   44.050839] EXT3-fs: mounted filesystem with ordered data mode.
[   44.080085] kjournald starting.  Commit interval 5 seconds
[   44.094803] EXT3 FS on hdd1, internal journal
[   44.094806] EXT3-fs: mounted filesystem with ordered data mode.
[   53.612003] NET: Registered protocol family 10
[   53.612089] lo: Disabled Privacy Extensions
[   53.612448] IPv6 over IPv4 tunneling driver[/FONT]
```and now it is```
[FONT="Courier New"][   34.253109] EXT3-fs: mounted filesystem with ordered data mode.
[   41.091135] Linux Tulip driver version 1.1.14 (May 6, 2006)
[   41.091889] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   41.091929] GSI 20 sharing vector 0xE9 and IRQ 20
[   41.091969] ACPI: PCI Interrupt 0000:03:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 233
[   41.092684] tulip0:  MII transceiver #1 config 1000 status 7849 advertising 01e1.
[   41.099258] eth1: ADMtek Comet rev 17 at Port 0xac00, 00:E0:4D:06:BC:4C, IRQ 233.
[   41.154516] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.171077] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.590935] FDC 0 is a post-1991 82077
[   41.610244] parport: PnPBIOS parport detected.
[   41.610333] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   42.024665] input: PC Speaker as /class/input/input1
[   42.300989] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[   42.301030] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 23 (level, low) -> IRQ 201
[   42.626594] intel8x0_measure_ac97_clock: measured 58805 usecs
[B][   42.626635] intel8x0: clocking to 47044
[  221.152550] lp0: using parport0 (interrupt-driven).[/B]
[  221.311033] it87: Found IT8712F chip at 0x290, revision 7
[  221.596800] Adding 570268k swap on /dev/disk/by-uuid/e918f20d-c70b-40b7-82f3-461714f7e23d.  Priority:-1 extents:1 across:570268k
[  221.746459] EXT3 FS on hda1, internal journal
[  222.002550] kjournald starting.  Commit interval 5 seconds
[  222.013709] EXT3 FS on hdc1, internal journal
[  222.035886] kjournald starting.  Commit interval 5 seconds
[  222.049691] EXT3 FS on hdd1, internal journal
[  222.049695] EXT3-fs: mounted filesystem with ordered data mode.
[  231.355060] NET: Registered protocol family 10
[  231.355177] lo: Disabled Privacy Extensions
[  231.355518] IPv6 over IPv4 tunneling driver[/FONT]
```

---

### Post by ibejohn on 2007-02-11
FYI

After doing a lot of investigation and searching I found that the problem was apparently udev related.  I saw the following post that sounded similar to what I was seeing:

[http://www.linuxquestions.org/questions/showthread.php?t=482136](http://www.linuxquestions.org/questions/showthread.php?t=482136)

At the end of the post the author said he solved his problems by following the advice of an IRC bot:
> <dpkg> extra, extra, read all about it, fresh udev config is when upgrading to a new major release of udev it is often beneficial to get fresh udev config files: dpkg -P --force-depends udev && apt-get install udevI did the same and now am back to 53 second boot times.

---

### Post by bl00dnu7 on 2007-02-23
Finally! the solution I've been searching for.  Thank you!
[http://bl00dnu7.net/blog/?p=231]("http://bl00dnu7.net/blog/?p=231")

---

### Post by disturbedite on 2007-02-23
i had this same problem.  i wasn't sure what caused it and i still have still have yet to see if this worked, but when i tried that i got this:

dpkg: udev: dependency problems, but removing anyway as you request:
 libgphoto2-2 depends on udev.
 mdadm depends on udev (>= 0.79-0ubuntu22).
 pcmciautils depends on udev.
 hal depends on udev (>= 0.065).
 libmtp2 depends on udev.
 libmtp5 depends on udev.
 initramfs-tools depends on udev (>= 0.086-1).
(Reading database ... 228204 files and directories currently installed.)
Removing udev ...
Purging configuration files for udev ...
dpkg - warning: while removing udev, directory `/lib/udev/devices/net' not empty so not removed.
dpkg - warning: while removing udev, directory `/lib/udev/devices' not empty so not removed.
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

so i reinstalled udev cuz it looked as if it didn't get reinstalled.  obviously it'd be foolish to reboot without udev installed.  :mrgreen:

---

### Post by bl00dnu7 on 2007-02-23
I got that same thing.  I think it's just because the second command is not run under sudo, so running it again makes everything great

Probably better instructions for Ubuntu are:
```
sudo dpkg -P --force-depends udev 
sudo apt-get install udev
```

---

### Post by disturbedite on 2007-02-23
oh duh!  i knew that.  happens sometimes.  so simple i overlooked it.  thanks for pointing that out.

---

### Post by disturbedite on 2007-02-24
UPDATE:  i'm sorry to say this didn't work for me.  it still takes me 2 minutes to boot up...  :(

---

