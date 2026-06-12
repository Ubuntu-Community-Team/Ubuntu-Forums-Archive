---
title: "boot hangs (sometimes) when mounting swap partition"
date: 2013-02-20
forum: General Help
---

### Post by bsieg on 2013-02-20
Hey gang, I'm having a weird problem with my swap partition with some of the recent kernel updates.  I'm running ubuntu 12.04 on a lenovo ideapad Z480 with linux kernel 3.2.0-xx, and upgrading the kernel I guess as they come out (I'm just doing what apt-get upgrade tells me to do).  Initially, I was able to boot normally every time, but starting with 3.2.0-33 (or so), it only boots about 1 of every 3 times, and trying to boot with 3.2.0-35 or later never boots at all.  

When it hangs, it gets stuck after printing: 
```

...
[    3.198739]  sda: sda1 sda2 sda3
[    3.200049] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.202136] Freeing unused kernel memory: 924k freed
[    3.203091] Write protecting the kernel read-only data: 12288k
[    3.207823] Freeing unused kernel memory: 1608k freed
[    3.211643] Freeing unused kernel memory: 1196k freed
[    3.227014] udevd[107]: starting version 175
[    3.236062] hub 1-1:1.0: USB hub found
[    3.237369] hub 1-1:1.0: 6 ports detected
[    3.251929] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.253168] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.255029] r8169 0000:02:00.0: setting latency timer to 64
[    3.255111] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    3.255541] r8169 0000:02:00.0: eth0: RTL8105e at 0xffffc90000c42000, 08:9e:01:2f:ea:15, XID 00c00000 IRQ 42
[    3.350626] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    3.483056] hub 2-1:1.0: USB hub found
[    3.484127] hub 2-1:1.0: 6 ports detected
[    3.650156] usb 3-3: new high-speed USB device number 2 using xhci_hcd

```

If the boot is successful, the next line in dmesg is: 
```

[   15.311677] Adding 6151164k swap on /dev/sda3.  Priority:-1 extents:1 across:6151164k

```

So it would seem that the problem has to do with mounting my swap partition (/dev/sda3), but only sometimes, and only with the recent kernel updates.  So my questions are:

[B]1. What the heck is going on?
2. Is it normal for it to take ~12 seconds to mount a swap partition?[/B]



Other stuff:
the entry in blkid:
```
/dev/sda3: UUID="3734c23e-e33d-469a-be28-983df41a1b57" TYPE="swap" 

```

the entry in /etc/fstab:
```

UUID=3734c23e-e33d-469a-be28-983df41a1b57 none swap sw 0 0

```

(they match!)

Also, I ran a self test with smartctl and it didn't show anything was wrong with my harddrive.  But I don't know if that's any definitive proof of anything

Thanks for your help!

---

