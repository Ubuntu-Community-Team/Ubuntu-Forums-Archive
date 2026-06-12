---
title: "USB Stick doesn't show up or get mounted anymore"
date: 2019-12-25
forum: General Help
---

### Post by Wa_Si on 2019-12-25
Hi I have an USB-Stick which worked some time ago but now it doesn't appear anymore.
I tried it on two differenc PCs, same behavior. Other USB-Devices get mounted automatically without any problem.

I'm using Ubuntu 18.04. But also on Windows PCs it doesn't show up.
The stick is an intenso 64 GB Stick (I think it is USB2)

I tried to find it in gparted, but it isn't listed there.

Here the lines from **/var/log/syslog** when I plug in the USB-Stick:

```

Dec 25 13:36:46 uT1500 kernel: [13919.073029] usb 2-1.4.3: new high-speed USB device number 8 using ehci-pci
Dec 25 13:36:47 uT1500 kernel: [13919.285843] usb 2-1.4.3: New USB device found, idVendor=ffff, idProduct=1201
Dec 25 13:36:47 uT1500 kernel: [13919.285847] usb 2-1.4.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Dec 25 13:36:47 uT1500 kernel: [13919.286351] usb-storage 2-1.4.3:1.0: USB Mass Storage device detected
Dec 25 13:36:47 uT1500 kernel: [13919.286545] scsi host7: usb-storage 2-1.4.3:1.0
Dec 25 13:36:47 uT1500 mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.3"
Dec 25 13:36:47 uT1500 mtp-probe: bus: 2, device: 8 was not an MTP device
Dec 25 13:36:47 uT1500 upowerd[1106]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.3/2-1.4.3:1.0
Dec 25 13:36:47 uT1500 upowerd[1106]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.3
Dec 25 13:36:48 uT1500 kernel: [13920.309871] scsi 7:0:0:0: Direct-Access     NAND     USB2DISK         0.00 PQ: 0 ANSI: 4
Dec 25 13:36:48 uT1500 kernel: [13920.310465] sd 7:0:0:0: Attached scsi generic sg5 type 0
Dec 25 13:36:48 uT1500 kernel: [13920.311778] sd 7:0:0:0: [sde] Attached SCSI removable disk

```


Can anyone help?
Thanks a lot.

---

### Post by yancek on 2019-12-25
Any hardware is going to fail eventually.  If you have tried it on multiple operating systems and multiple computers, I would think it likely  that it has failed.  What exactly is on the usb?  What filesystem type, is it just data?

---

### Post by CelticWarrior on 2019-12-25
> **Wa_Si said:**
> I'm using Ubuntu 18.04. But also on Windows PCs it doesn't show up.
The stick is an intenso 64 GB Stick (I think it is USB2)


I would say with a very high degree of confidence that that hardware is as good as dead.

---

### Post by bunny9000 on 2019-12-25
If there are no lights and no one is home then it's probably gone to silicon heaven. At least it's only a cheap replacement.

But if you want to troubleshoot I'd recommend plugging it into a computer and seeing if the BIOS detects it under the boot devices section. That's the highest chance of finding if it's alive on the hardware level. But if it was in an NTFS, FAT or EXT format linux would read all the listed file systems and windows would read the fat and ntfs file systems.

I don't recall if Linux can read mac formatted usb drives.

---

### Post by Wa_Si on 2019-12-26
Hi all, thanks for your replies.

> **yancek said:**
> Any hardware is going to fail eventually.  If you have tried it on multiple operating systems and multiple computers, I would think it likely  that it has failed.  What exactly is on the usb?  What filesystem type, is it just data?
It was fat-filesystem and it was only data. Nothing unusual.

> **bunny9000 said:**
> If there are no lights and no one is home then it's probably gone to silicon heaven. At least it's only a cheap replacement.

But if you want to troubleshoot I'd recommend plugging it into a computer and seeing if the BIOS detects it under the boot devices section. That's the highest chance of finding if it's alive on the hardware level. But if it was in an NTFS, FAT or EXT format linux would read all the listed file systems and windows would read the fat and ntfs file systems.

I don't recall if Linux can read mac formatted usb drives.
In Bios it was listed as a boot device. So I'm not sure if it is really dead, or it has just defect partition table or something like that.

Anyways, I think I won't spend any more time with this problem. The last time I tried to rescue an USB-Stick I wasted days in it, but in the end It was just not repairable.

Thanks again for the hints.

---

