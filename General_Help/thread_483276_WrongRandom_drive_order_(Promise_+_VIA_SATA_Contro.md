---
title: "Wrong/Random drive order (Promise + VIA SATA Controller on ASUS A8V)"
date: 2007-06-24
forum: General Help
---

### Post by sander2 on 2007-06-24
Hi!

Yesterday i migrated my home-server from Gentoo to Ubuntu. Now I'm expiriencing a very strange behaviour:

I have a ASUS A8V Deluxe Mainboard. It has two SATA Controller on-board. One is Promise FastTrack 20378, the other is a VIA VT 8237. In the BIOS i set the "Hard Drive Order" to

1. Promise Drive #1
2. Promise Drive #2
3. VIA Drive #1
4. VIA Drive #2

I installed Ubuntu Feisty on the 2 Drives connected to the Promise Controller using Software RAID1 (not fakeRaid). Everything worked flawlessly.

But now, when I reboot the System the Drive order seems to randomly change! Sometimes it works as expected (Promise Drives being /dev/sda and /dev/sdb, VIA Drives being /dev/sdc and /dev/sdd) and sometimes the drive order changes to VIA being the "first" controller, resulting in a wrong layout (Disk connected to Promise become /dev/sdc and /dev/sdd, Disks connected to VIA become /dev/sda and /dev/sdb)

The system still boots up because /etc/fstab uses the Drive ID's and not the Device links. Nevertheless I would like my drives to appear in the same order everytime.

This isn't a "normal" behaviour, is it?

cheers,
Sander

---

### Post by rampage on 2007-07-04
I have this same problem its a pain in the ***

I wish I could figure it out

*bump*

---

### Post by kingneutron on 2008-04-22
This is a big pain for me as well.  Was running 6.10 (64-bit) up until last week, then they end-of-lifed it and I upgraded to 7.04...

Now my hard drive order is different.  I have a PCI RAID card and 7.04 thinks the drive on there takes a higher priority than the MOTHERBOARD SATA CONTROLLER. :(

Ubuntu Needs to find a way to change, or stabilize, the module load order so the motherboard gets priority.  LSPCI makes this pretty clear:

```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GS (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
07:03.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 02)
07:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

Why in the world would you want to load the PCI card before the motherboard??

> **sander2 said:**
> Hi!

Yesterday i migrated my home-server from Gentoo to Ubuntu. Now I'm expiriencing a very strange behaviour:

I have a ASUS A8V Deluxe Mainboard. It has two SATA Controller on-board. One is Promise FastTrack 20378, the other is a VIA VT 8237. In the BIOS i set the "Hard Drive Order" to

1. Promise Drive #1
2. Promise Drive #2
3. VIA Drive #1
4. VIA Drive #2

I installed Ubuntu Feisty on the 2 Drives connected to the Promise Controller using Software RAID1 (not fakeRaid). Everything worked flawlessly.

But now, when I reboot the System the Drive order seems to randomly change! Sometimes it works as expected (Promise Drives being /dev/sda and /dev/sdb, VIA Drives being /dev/sdc and /dev/sdd) and sometimes the drive order changes to VIA being the "first" controller, resulting in a wrong layout (Disk connected to Promise become /dev/sdc and /dev/sdd, Disks connected to VIA become /dev/sda and /dev/sdb)

The system still boots up because /etc/fstab uses the Drive ID's and not the Device links. Nevertheless I would like my drives to appear in the same order everytime.

This isn't a "normal" behaviour, is it?

cheers,
Sander

---

### Post by kingneutron on 2008-04-22
* Note: AFAIK, this only applies to Ubuntu 7.04.

--After doing a couple of hours of research, I fixed the SATA disk boot order (hopefully):

o Found out the new " initrd " format is actually a CPIO.gz archive, and not mountable directly; you used to be able to loop mount it. See:

**[COLOR="Blue"][http://www.linuxjournal.com/article/9452](http://www.linuxjournal.com/article/9452)[/COLOR]**

--Rather than goofing around with a one-shot fix that won't translate to kernel upgrades, I poked around a bit.  Midnight Commander (' mc ') can work directly on files with a .cpio extension, so here's the short form of what I did:

' cd /boot '
' gzip -cd initrd.img-2.6.20-16-server > initrd.cpio '

' mc ' [COLOR="Red"]# Hit Enter on the initrd.cpio file, and MC will drop into it the same as a .tar or .zip file -- Virtual Directory is your friend ;-)[/COLOR]

--Poking around in the .cpio file, I found the **" /scripts/functions " ** file, which has a section at the end where it loads CUSTOM MODULES FIRST.

--So I modified **" /usr/share/initramfs-tools/modules "** and added **" ata_generic "** at the end so it loads the motherboard SATA driver first.

--Then I had to regenerate the initramfs:

' update-initramfs -u '
' reboot '

--Hopefully this fixed it; if not, will report back.

> **kingneutron said:**
> This is a big pain for me as well.  Was running 6.10 (64-bit) up until last week, then they end-of-lifed it and I upgraded to 7.04...

Now my hard drive order is different.  I have a PCI RAID card and 7.04 thinks the drive on there takes a higher priority than the MOTHERBOARD SATA CONTROLLER. :(

Ubuntu Needs to find a way to change, or stabilize, the module load order so the motherboard gets priority.  LSPCI makes this pretty clear:

```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GS (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
07:03.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 02)
07:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

Why in the world would you want to load the PCI card before the motherboard??

---

