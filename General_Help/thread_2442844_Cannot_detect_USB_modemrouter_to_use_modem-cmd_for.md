---
title: "Cannot detect USB modem/router to use modem-cmd for AT commands"
date: 2020-05-08
forum: General Help
---

### Post by MimziM on 2020-05-08
I need to Identify my device to use modem-cmd. I need to be able to send AT+ commands
The syntax is : sudo modem-cmd [device] [command]
However I can't identify the device.
```
sudo dmesg|grep tty
```
returns
```
[    0.108927] printk: console [tty0] enabled

```
My device is a ZTE MF927U LTE Ufi mobile router
```
pantera@BadAss:~/Desktop$ sudo dmesg|grep ZTE
[  462.349895] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  466.146618] cdc_ether 2-1.2:1.0 eth0: register 'cdc_ether' at usb-0000:00:1d.0-1.2, ZTE CDC Ethernet Device, 00:a0:c6:00:00:00
[  466.926746] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  699.051935] cdc_ether 2-1.2:1.0 enx00a0c6000000: unregister 'cdc_ether' usb-0000:00:1d.0-1.2, ZTE CDC Ethernet Device
[  707.245999] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  710.927309] cdc_ether 2-1.2:1.0 eth0: register 'cdc_ether' at usb-0000:00:1d.0-1.2, ZTE CDC Ethernet Device, 00:a0:c6:00:00:00
[  711.950344] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  717.226971] cdc_ether 2-1.2:1.0 enx00a0c6000000: unregister 'cdc_ether' usb-0000:00:1d.0-1.2, ZTE CDC Ethernet Device
[  718.766055] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  722.277581] cdc_ether 2-1.2:1.0 eth0: register 'cdc_ether' at usb-0000:00:1d.0-1.2, ZTE CDC Ethernet Device, 00:a0:c6:00:00:00
[  723.310235] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[ 1182.375845] cdc_ether 2-1.2:1.0 enx00a0c6000000: unregister 'cdc_ether' usb-0000:00:1d.0-1.2, ZTE CDC Ethernet Device
[ 1186.221648] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[ 1189.700546] cdc_ether 2-1.2:1.0 eth0: register 'cdc_ether' at usb-0000:00:1d.0-1.2, ZTE CDC Ethernet Device, 00:a0:c6:00:00:00
[ 1190.733646] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[ 1199.058047] cdc_ether 2-1.2:1.0 enx00a0c6000000: unregister 'cdc_ether' usb-0000:00:1d.0-1.2, ZTE CDC Ethernet Device
[ 1204.204195] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[ 1221.931091] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[ 1225.449097] cdc_ether 2-1.2:1.0 eth0: register 'cdc_ether' at usb-0000:00:1d.0-1.2, ZTE CDC Ethernet Device, 00:a0:c6:00:00:00
[ 1226.475104] scsi 6:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
pantera@BadAss:~/Desktop$ 

```

Any advice would be appreciated

---

