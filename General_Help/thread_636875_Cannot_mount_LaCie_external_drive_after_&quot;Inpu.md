---
title: "Cannot mount LaCie external drive after &quot;Input/Output errors"
date: 2007-12-10
forum: General Help
---

### Post by Roobert on 2007-12-10
Hi, I was writing some data to my external LaCie 2 terabyte drive, when I ran into all kinds of "Input/Output errors". I was using ntfs-3g version 1.1120. Windows cannot even detect this drive anymore; whether I turn it on and off, plug it in to different USB ports on my machine, use different USB cables, the result is the same. I don't even think I can use the mount command, as I can't see anything in /dev remotely resembling my external drive.

I noticed all kinds of error messages in /var/log/syslog:
```
Dec 10 08:00:58 localhost kernel: [229633.096428] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:00:58 localhost kernel: [229633.096461] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:00:59 localhost kernel: [229633.594870] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:01:00 localhost kernel: [229634.819760] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 10 08:01:04 localhost kernel: [229638.809655] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 10 08:01:04 localhost kernel: [229639.081241] ieee1394: Speed probe of node 0-00:1023 yields S400
Dec 10 08:01:04 localhost kernel: [229639.081246] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:01:04 localhost kernel: [229639.081466] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:01:04 localhost kernel: [229639.483951] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:01:13 localhost kernel: [229647.747020] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 10 08:01:13 localhost kernel: [229648.018642] ieee1394: Speed probe of node 0-00:1023 yields S400
Dec 10 08:01:13 localhost kernel: [229648.018647] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:01:13 localhost kernel: [229648.018867] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:01:14 localhost kernel: [229648.604855] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:01:19 localhost kernel: [229653.688275] ieee1394: Speed probe of node 0-00:1023 yields S400
Dec 10 08:01:19 localhost kernel: [229653.688280] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:01:19 localhost kernel: [229653.688314] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:01:19 localhost kernel: [229654.110911] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:01:26 localhost kernel: [229661.416403] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 10 08:01:30 localhost kernel: [229665.350438] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 10 08:01:32 localhost kernel: [229667.054422] ieee1394: Speed probe of node 0-00:1023 yields S400
Dec 10 08:01:32 localhost kernel: [229667.054428] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:01:32 localhost kernel: [229667.054461] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:01:33 localhost kernel: [229667.520948] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:01:34 localhost kernel: [229668.745839] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 10 08:01:35 localhost kernel: [229669.695409] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:01:35 localhost kernel: [229670.373691] ieee1394: Error parsing configrom for node 0-01:1023
Dec 10 08:01:35 localhost kernel: [229670.373701] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[55aa55aa55aa55aa]
Dec 10 08:01:36 localhost kernel: [229670.645312] ieee1394: Speed probe of node 0-00:1023 yields S400
Dec 10 08:01:36 localhost kernel: [229670.645316] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:01:36 localhost kernel: [229670.645349] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:01:36 localhost kernel: [229670.645358] ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[55aa55aa55aa55aa]
Dec 10 08:01:36 localhost kernel: [229671.032054] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:01:49 localhost kernel: [229683.919723] ieee1394: Speed probe of node 0-00:1023 yields S400
Dec 10 08:01:49 localhost kernel: [229683.919728] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:01:49 localhost kernel: [229683.919761] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:01:50 localhost kernel: [229684.733361] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:01:51 localhost kernel: [229685.958529] ieee1394: Speed probe of node 0-00:1023 yields S400
Dec 10 08:01:51 localhost kernel: [229685.958534] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:01:51 localhost kernel: [229685.958576] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:01:52 localhost kernel: [229686.512854] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:01:57 localhost kernel: [229692.338088] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 10 08:01:58 localhost kernel: [229693.287658] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:01:59 localhost kernel: [229693.965940] ieee1394: Error parsing configrom for node 0-01:1023
Dec 10 08:01:59 localhost kernel: [229693.965950] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[55aa55aa55aa55aa]
Dec 10 08:02:00 localhost kernel: [229694.441059] ieee1394: Speed probe of node 0-00:1023 yields S400
Dec 10 08:02:00 localhost kernel: [229694.441065] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:02:00 localhost kernel: [229694.441097] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:02:00 localhost kernel: [229694.441105] ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[55aa55aa55aa55aa]
Dec 10 08:02:00 localhost kernel: [229694.736019] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:02:03 localhost kernel: [229698.367179] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 10 08:02:04 localhost kernel: [229699.316390] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:02:05 localhost kernel: [229699.994673] ieee1394: Error parsing configrom for node 0-01:1023
Dec 10 08:02:05 localhost kernel: [229699.994683] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[55aa55aa55aa55aa]
Dec 10 08:02:06 localhost kernel: [229700.469798] ieee1394: Speed probe of node 0-00:1023 yields S400
Dec 10 08:02:06 localhost kernel: [229700.469803] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:02:06 localhost kernel: [229700.469837] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:02:06 localhost kernel: [229700.469844] ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[55aa55aa55aa55aa]
Dec 10 08:02:06 localhost kernel: [229700.748797] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:02:07 localhost kernel: [229701.973688] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 10 08:02:09 localhost kernel: [229703.693635] ieee1394: Speed probe of node 0-00:1023 yields S400
Dec 10 08:02:09 localhost kernel: [229703.693640] ieee1394: Error parsing configrom for node 0-00:1023
Dec 10 08:02:09 localhost kernel: [229703.693673] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 10 08:02:09 localhost kernel: [229704.403540] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 10 08:02:11 localhost kernel: [229705.652377] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
```


Any ideas on how I can detect/repair/mount this drive? Thanks!

~ Eric.

---

### Post by Roobert on 2007-12-10
Here is my fstab:

```
proc    /proc   proc    defaults        0       0
#Entry for /dev/sda3 :
UUID=814bd08e-7693-4789-bf89-5433e7d10728       /       ext3    defaults,errors=remount-ro      0       1
#Entry for /dev/sda5 :
UUID=635e9522-05a1-49a1-b6a5-467edaff485b       /home   ext3    defaults        0       2
#Entry for /dev/sda1 :
UUID=07D5-0304  /media/sda1     vfat    defaults,utf8,umask=007,gid=46  0       1
#Entry for /dev/sda2 :
UUID=A894E3B694E384E2   /media/windows  ntfs-3g defaults,locale=en_CA.UTF-8     0       0
#Entry for /dev/sda6 :
UUID=0e5a9a58-94b1-424f-bb26-dce6a3cf46a9       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto     0       0
UUID=EE7EDFB77EDF7735   /media/LaCie_2TB        ntfs-3g defaults,locale=en_CA.UTF-8     0       0
```

---

### Post by Roobert on 2007-12-10
Here's something really weird; when I turn the LaCie drive on, I get the following output from /var/log/syslog:

```

Dec 10 11:54:40 localhost kernel: [ 2268.284709] usb 5-5: new high speed USB device using ehci_hcd and address 6
Dec 10 11:54:40 localhost kernel: [ 2268.418166] usb 5-5: configuration #1 chosen from 1 choice
Dec 10 11:54:40 localhost NetworkManager: <debug> [1197302080.307336] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_6250_AAC5B6892C14'). 
Dec 10 11:54:40 localhost NetworkManager: <debug> [1197302080.364193] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_6250_AAC5B6892C14_if0'). 
Dec 10 11:54:40 localhost NetworkManager: <debug> [1197302080.397503] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_6250_AAC5B6892C14_usbraw'). 
```

But the drive doesn't mount, nor can I find any entry in /dev that might indicate the drive is being detected. Does this information help any?

~ Eric.

---

### Post by geraldm on 2007-12-10
This may not help, but I would point out that there is inconsistency in the documentation for ntfs although I see you are using ntfs-3g, 
In the vanilla linux kernel source TOPDIR/Documentation/filesystems/ntfs.txt it points out that that filesystem has mount options that I do not see documented elsewhere (as in man mount)

sloppy=<BOOL>   If sloppy is specified, ignore unknown mount options.
      Otherwise the default behaviour is to abort mount if
      any unknown options are found.

Gerald

---

