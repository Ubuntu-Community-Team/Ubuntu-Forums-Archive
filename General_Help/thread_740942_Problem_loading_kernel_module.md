---
title: "Problem loading kernel module"
date: 2008-03-31
forum: General Help
---

### Post by mgazb on 2008-03-31
I have eventually managed to compile a driver for a new PCI card on Ubuntu 7.10. with 2.6.24 kernel.

It has previously been built and run under Fedora 7 with 2.6.24.3 kernel.

There is an install script that comes with the SDK

```


module="tmman1300.ko"
name="pnx1300"
device="pnx1300"
mode="666"
major="240"

# invoke insmod with all the arguments
/sbin/insmod ./$module || exit 1

# remove stale node
rm -f /dev/$device

major=`awk "\\$2==\"$name\" {print \\$1}" /proc/devices`

mknod /dev/$device c $major 0

# give appropriate permissions
chmod $mode /dev/$device


```

The problem is that the device does not appear in /proc/devices. Does this mean that insmod has failed? Does Ubuntu use a different device file?

```

root@io:~/kernelmode# cat /proc/devices
Character devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 29 fb
 99 ppdev
128 ptm
136 pts
171 ieee1394
180 usb
189 usb_device
216 rfcomm
226 drm
254 usb_endpoint

Block devices:
  1 ramdisk
  2 fd
  3 ide0
 22 ide1

```

the driver does appear in /proc/modules

```

root@io:~/kernelmode# cat /proc/modules
tmman1300 99900 0 - Live 0xcfb5a000 (P)
ipv6 266884 8 - Live 0xcfba7000
af_packet 23684 2 - Live 0xcfb49000
via 43520 2 - Live 0xcfb33000
drm 81684 3 via, Live 0xcfb1e000
rfcomm 41744 2 - Live 0xcfb9b000
l2cap 25856 11 rfcomm, Live 0xcfb10000
bluetooth 60644 4 rfcomm,l2cap, Live 0xcfc04000
ppdev 10500 0 - Live 0xcfb0c000
cpufreq_stats 7360 0 - Live 0xcfb1b000
cpufreq_powersave 2944 0 - Live 0xcf860000
cpufreq_ondemand 9868 0 - Live 0xcfaf8000
cpufreq_userspace 5540 0 - Live 0xcfaf5000
cpufreq_conservative 8968 0 - Live 0xcfaf1000
freq_table 5920 2 cpufreq_stats,cpufreq_ondemand, Live 0xcfb01000
dock 11408 0 - Live 0xcfaed000
sbs 15496 0 - Live 0xcfae8000
ac 7172 0 - Live 0xcfafe000
sbshc 7936 1 sbs, Live 0xcfb09000
container 5888 0 - Live 0xcf9ca000
battery 14596 0 - Live 0xcfb04000
sbp2 24456 0 - Live 0xcf9c3000
lp 12580 0 - Live 0xcf999000
parport_pc 37284 1 - Live 0xcf9b8000
parport 37832 3 ppdev,lp,parport_pc, Live 0xcf9ad000
psmouse 40592 0 - Live 0xcf9a2000
serio_raw 8196 0 - Live 0xcf995000
pcspkr 4224 0 - Live 0xcf992000
i2c_viapro 9748 0 - Live 0xcf98e000
i2c_core 24960 1 i2c_viapro, Live 0xcf986000
button 9488 0 - Live 0xcf99e000
shpchp 34708 0 - Live 0xcf97c000
pci_hotplug 31136 1 shpchp, Live 0xcf973000
via_agp 11264 0 - Live 0xcf91c000
agpgart 34888 2 drm,via_agp, Live 0xcf95c000
evdev 12928 4 - Live 0xcf917000
ext3 136328 2 - Live 0xcf939000
jbd 48788 1 ext3, Live 0xcf92c000
mbcache 9856 1 ext3, Live 0xcf84a000
ide_cd 40736 0 - Live 0xcf968000
cdrom 37280 1 ide_cd, Live 0xcf90c000
ide_disk 17280 4 - Live 0xcf906000
floppy 59204 0 - Live 0xcf8f6000
via82cxxx 9604 0 [permanent], Live 0xcf862000
ide_core 112332 3 ide_cd,ide_disk,via82cxxx, Live 0xcf8d9000
ehci_hcd 37132 0 - Live 0xcf921000
uhci_hcd 26768 0 - Live 0xcf89d000
ata_generic 8580 0 - Live 0xcf85c000
ohci1394 34096 0 - Live 0xcf850000
usbcore 146156 3 ehci_hcd,uhci_hcd, Live 0xcf8b4000
libata 159344 1 ata_generic, Live 0xcf9ce000
scsi_mod 151692 2 sbp2,libata, Live 0xcf876000
ieee1394 93880 2 sbp2,ohci1394, Live 0xcf832000
8139too 27392 0 - Live 0xcf86e000
8139cp 24832 0 - Live 0xcf866000
mii 6784 2 8139too,8139cp, Live 0xcf828000
thermal 17052 0 - Live 0xcf822000
processor 36808 1 thermal, Live 0xcf818000
fan 5892 0 - Live 0xcf82c000
fuse 50708 1 - Live 0xcf8a6000

```

Also, if I try to run rmmod the system hangs - I'm not sure whether it will come back after a log time. Is this another symptom of the problem with /proc/devices?

thanks

dan

---

