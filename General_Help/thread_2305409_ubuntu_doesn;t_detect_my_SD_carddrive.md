---
title: "ubuntu doesn;t detect my SD card/drive"
date: 2015-12-05
forum: General Help
---

### Post by jj4 on 2015-12-05
When I put SD cards into the SD slot nothing happens.
I ran this but still nothing:
sudo modprobe -r r852; sudo modprobe -r sdhci_pci; sudo modprobe r852; sudo modprobe sdhci_pci

Here is the lspic -v results:

[http://pastebin.com/kQaHZzLi](http://pastebin.com/kQaHZzLi)

---

### Post by sudodus on 2015-12-05
You can use the following commands to find out if the SD card is recognized as a mass storage device and if there is some partition with a file system.

```

sudo parted -ls
sudo lsblk -fm
```

Please post the output in a reply!

---

### Post by jj4 on 2015-12-05
doesn't seem like it, there should be a 16gb drive there

```

j@j-Aspire-5610:~$ sudo parted -ls
[sudo] password for j: 
Model: ATA WDC WD2500BEVS-2 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  73.4GB  73.4GB  primary  ntfs         boot
 2      73.4GB  147GB   73.4GB  primary  ntfs
 3      147GB   250GB   103GB   primary  ext4


j@j-Aspire-5610:~$ sudo lsblk -fm
NAME   FSTYPE LABEL   UUID                                 MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                                                   sda    232.9G root  disk  brw-rw----
&#9500;&#9472;sda1 ntfs           5D34D268177B47F4                                &#9500;&#9472;sda1  68.4G root  disk  brw-rw----
&#9500;&#9472;sda2 ntfs   Trading 39B76B7A421D646B                                &#9500;&#9472;sda2  68.4G root  disk  brw-rw----
&#9492;&#9472;sda3 ext4           bd206689-5478-43d0-bc8d-e91c05514cde /          &#9492;&#9472;sda3  96.2G root  disk  brw-rw----
sr0                                                                   sr0     1024M root  cdrom brw-rw----
j@j-Aspire-5610:~$ 

```

---

### Post by matt_symes on 2015-12-05
Hi

Open a terminal and type

```
tail -f /var/log/syslog
```

Insert the SD card into the controller, wait 5 seconds, and post the output tail followed from syslog back here.

That may give some clues as to what is happening.

Kind regards

---

### Post by sudodus on 2015-12-05
That right. It is not recognized as a mass storage device. Most card readers are recognized by linux, but not all.

I don't know the ENE Technology Inc ENE PCI Secure Digital Card Reader Controller.

- How new is the computer?

- And how new is the operating system, which version of Ubuntu?

Maybe you can try with a newer or older version of Ubuntu - and hope that there is a driver for your card reader.

---

### Post by jj4 on 2015-12-05
> **matt_symes said:**
> Hi

Open a terminal and type

```
tail -f /var/log/syslog
```

Insert the SD card into the controller, wait 5 seconds, and post the output tail followed from syslog back here.

That may give some clues as to what is happening.

Kind regards

one card posts nothing...the other posts:
The card definitely works as I have osmc running on the raspberry pi on it.
```

Dec  5 17:03:44 j-Aspire-5610 kernel: [ 4411.287012] mmc1: new high speed SDHC card at address 0001
Dec  5 17:03:44 j-Aspire-5610 kernel: [ 4411.312180] Driver 'mmcblk' needs updating - please use bus_type methods
Dec  5 17:03:44 j-Aspire-5610 kernel: [ 4411.312310] mmcblk0: mmc1:0001 00000 14.6 GiB 
Dec  5 17:03:44 j-Aspire-5610 kernel: [ 4411.314383] mmcblk0: error -123 sending status command, retrying
Dec  5 17:03:44 j-Aspire-5610 kernel: [ 4411.314401] mmcblk0: error -123 sending status command, retrying
Dec  5 17:03:44 j-Aspire-5610 kernel: [ 4411.314416] mmcblk0: error -123 sending status command, aborting
Dec  5 17:03:44 j-Aspire-5610 kernel: [ 4411.314543] ldm_validate_partition_table(): Disk read failed.
Dec  5 17:03:44 j-Aspire-5610 kernel: [ 4411.314663] Dev mmcblk0: unable to read RDB block 0
Dec  5 17:03:44 j-Aspire-5610 kernel: [ 4411.314801]  mmcblk0: unable to read partition table
Dec  5 17:03:44 j-Aspire-5610 kernel: [ 4411.508161] mmc1: card 0001 removed


```

---

### Post by matt_symes on 2015-12-05
Hi

As an addendum to sudodus' post, have you eliminated failing hardware or loose cables ?

Kind regards

---

### Post by jj4 on 2015-12-05
> **matt_symes said:**
> Hi

As an addendum to sudodus' post, have you eliminated failing hardware or loose cables ?

Kind regards

Card1 works as it runs osmc successfully.
Card 2 shows up in Windows.
There are no external cables as it is a SD card - internal maybe but it's recognising something was inserted so should be fine.

---

### Post by matt_symes on 2015-12-05
Hi

Can you post the output of this command.

```
lsmod | egrep "sdhci_pci|r852"
```

Is there any reason you are loading the r852 kernel driver ? You don't seem to have a ricoh reader.
```

06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Device 0090
        Flags: medium devsel, IRQ 17
        Memory at d0103400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci
```
```

matthew-xu-16-04:/lib/udev:2 % modinfo r852                          
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/mtd/nand/r852.ko
description:    Ricoh 85xx xD/smartmedia card reader driver
author:         Maxim Levitsky <maximlevitsky@gmail.com>
license:        GPL
srcversion:     8BD33E155C7F45AD5104169
alias:          pci:v00001180d00000852sv*sd*bc*sc*i*
depends:        sm_common,nand
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           r852_enable_dma:Enable usage of the DMA (default) (bool)
parm:           debug:Debug level (0-2) (int)
matthew-xu-16-04:/lib/udev:2 
```

Kind regards

---

### Post by jj4 on 2015-12-05
> **matt_symes said:**
> Hi

Can you post the output of this command.

```
lsmod | egrep "sdhci_pci|r852"
```

Is there any reason you are loading the r852 kernel driver ? You don't seem to have a ricoh reader.
```

06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Device 0090
        Flags: medium devsel, IRQ 17
        Memory at d0103400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci
```
```

matthew-xu-16-04:/lib/udev:2 % modinfo r852                          
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/mtd/nand/r852.ko
description:    Ricoh 85xx xD/smartmedia card reader driver
author:         Maxim Levitsky <maximlevitsky@gmail.com>
license:        GPL
srcversion:     8BD33E155C7F45AD5104169
alias:          pci:v00001180d00000852sv*sd*bc*sc*i*
depends:        sm_common,nand
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           r852_enable_dma:Enable usage of the DMA (default) (bool)
parm:           debug:Debug level (0-2) (int)
matthew-xu-16-04:/lib/udev:2 
```

Kind regards

I haven't changed anything so it seems tgat is what Ubuntu is loading by default.
Computer is an Acre Aspire 5610.

output:
```

j@j-Aspire-5610:~$ lsmod | egrep "sdhci_pci|r852"
sdhci_pci              20480  0 
sdhci                  45056  1 sdhci_pci
r852                   20480  0 
sm_common              20480  1 r852
nand                   69632  2 r852,sm_common
j@j-Aspire-5610:~$ 

```

---

### Post by matt_symes on 2015-12-05
Hi

> **jj4 said:**
> I haven't changed anything so it seems tgat is what Ubuntu is loading by default.

Are you sure about that ? I only listed 1 of your devices but none of them look to be a Ricoh device. I cannot see a device that would use r852. 

I can't find the full specification of the reader though so i could well be wrong.

> Computer is an Acre Aspire 5610.

output:
```

j@j-Aspire-5610:~$ lsmod | egrep "sdhci_pci|r852"
sdhci_pci              20480  0 
sdhci                  45056  1 sdhci_pci
r852                   20480  0 
sm_common              20480  1 r852
nand                   69632  2 r852,sm_common
j@j-Aspire-5610:~$ 

```

We may be able to get more debug information from dmesg.

```
dmesg | egrep "r852|sdhci"
```

Post the output back here.

What i would do is to remove the r852 kernel module and reload the sdhci_pci in case there's some conflict.

```
sudo modprobe -r r852 && sudo modprobe -r sdhci_pci && sudo modprobe sdhci_pci
```

```
tail -f /var/log/syslog
```

Put the sdcard in and post back the output from syslog here.

Kind regards

---

### Post by jj4 on 2015-12-06
> **matt_symes said:**
> Hi



Are you sure about that ? I only listed 1 of your devices but none of them look to be a Ricoh device. I cannot see a device that would use r852. 

I can't find the full specification of the reader though so i could well be wrong.



We may be able to get more debug information from dmesg.

```
dmesg | egrep "r852|sdhci"
```

Post the output back here.

```

j@j-Aspire-5610:~$ dmesg | egrep "r852|sdhci"
[    2.562494] sdhci: Secure Digital Host Controller Interface driver
[    2.562498] sdhci: Copyright(c) Pierre Ossman
[    2.570573] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[    2.570606] sdhci-pci 0000:06:04.2: enabling device (0000 -> 0002)
[    2.570736] sdhci-pci 0000:06:04.2: No vmmc regulator found
[    2.570740] sdhci-pci 0000:06:04.2: No vqmmc regulator found
[    2.592147] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[    2.592161] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)
[    2.592305] sdhci-pci 0000:06:04.4: No vmmc regulator found
[    2.592309] sdhci-pci 0000:06:04.4: No vqmmc regulator found
[  470.491316] sdhci: Secure Digital Host Controller Interface driver
[  470.491321] sdhci: Copyright(c) Pierre Ossman
[  470.500738] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[  470.500893] sdhci-pci 0000:06:04.2: No vmmc regulator found
[  470.500898] sdhci-pci 0000:06:04.2: No vqmmc regulator found
[  470.503018] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[  470.503152] sdhci-pci 0000:06:04.4: No vmmc regulator found
[  470.503156] sdhci-pci 0000:06:04.4: No vqmmc regulator found
j@j-Aspire-5610:~$ 


```
> 

What i would do is to remove the r852 kernel module and reload the sdhci_pci in case there's some conflict.

```
sudo modprobe -r r852 && sudo modprobe -r sdhci_pci && sudo modprobe sdhci_pci
```

```
tail -f /var/log/syslog
```

Put the sdcard in and post back the output from syslog here.

Kind regards

ok, now it works on one of the drives but not the other:

```

j@j-Aspire-5610:~$ tail -f /var/log/syslog
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.614516] sdhci: Secure Digital Host Controller Interface driver
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.614521] sdhci: Copyright(c) Pierre Ossman
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.623230] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.625769] sdhci-pci 0000:06:04.2: No vmmc regulator found
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.625776] sdhci-pci 0000:06:04.2: No vqmmc regulator found
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.628659] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.628719] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.628893] sdhci-pci 0000:06:04.4: No vmmc regulator found
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.628897] sdhci-pci 0000:06:04.4: No vqmmc regulator found
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.630459] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
Dec  6 01:07:46 j-Aspire-5610 kernel: [33453.091240] mmc1: new high speed SDHC card at address 0007
Dec  6 01:07:46 j-Aspire-5610 kernel: [33453.092898] mmcblk0: mmc1:0007 SD32G 28.9 GiB 
Dec  6 01:07:46 j-Aspire-5610 kernel: [33453.095579]  mmcblk0: p1
Dec  6 01:07:46 j-Aspire-5610 udisksd[1562]: Mounted /dev/mmcblk0p1 at /media/j/JPI on behalf of uid 1000
Dec  6 01:07:46 j-Aspire-5610 gnome-session[1359]: (nautilus:7925): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Dec  6 01:07:46 j-Aspire-5610 gnome-session[1359]: (nautilus:7925): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Dec  6 01:07:46 j-Aspire-5610 gnome-session[1359]: (nautilus:7925): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Dec  6 01:07:46 j-Aspire-5610 dbus[597]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Dec  6 01:07:46 j-Aspire-5610 systemd[1]: Starting Hostname Service...
Dec  6 01:07:47 j-Aspire-5610 dbus[597]: [system] Successfully activated service 'org.freedesktop.hostname1'
Dec  6 01:07:47 j-Aspire-5610 systemd[1]: Started Hostname Service.
Dec  6 01:07:50 j-Aspire-5610 kernel: [33457.692148] mmc1: card 0007 removed
Dec  6 01:07:50 j-Aspire-5610 udisksd[1562]: Cleaning up mount point /media/j/JPI (device 179:1 no longer exist)
Dec  6 01:07:50 j-Aspire-5610 systemd[1]: Unmounting /media/j/JPI...
Dec  6 01:07:50 j-Aspire-5610 umount[7937]: umount: /media/j/JPI: not mounted
Dec  6 01:07:50 j-Aspire-5610 systemd[1]: media-j-JPI.mount mount process exited, code=exited status=32
Dec  6 01:07:50 j-Aspire-5610 systemd[1]: Unmounted /media/j/JPI.
Dec  6 01:07:50 j-Aspire-5610 systemd[1]: Unit media-j-JPI.mount entered failed state.
Dec  6 01:07:50 j-Aspire-5610 kernel: [33457.744257] FAT-fs (mmcblk0p1): unable to read boot sector to mark fs as dirty
Dec  6 01:07:57 j-Aspire-5610 kernel: [33465.051216] mmc1: new high speed SDHC card at address 0007
Dec  6 01:07:57 j-Aspire-5610 kernel: [33465.051492] mmcblk0: mmc1:0007 SD32G 28.9 GiB 
Dec  6 01:07:57 j-Aspire-5610 kernel: [33465.053931]  mmcblk0: p1
Dec  6 01:07:58 j-Aspire-5610 systemd[1]: media-j-JPI.mount failed to run 'mount' task: No such file or directory
Dec  6 01:07:58 j-Aspire-5610 systemd[1]: Failed to mount /media/j/JPI.
Dec  6 01:07:58 j-Aspire-5610 systemd[1]: Mounting /media/j/JPI...
Dec  6 01:07:58 j-Aspire-5610 kernel: [33465.608461] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Dec  6 01:07:58 j-Aspire-5610 udisksd[1562]: Mounted /dev/mmcblk0p1 at /media/j/JPI1 on behalf of uid 1000
Dec  6 01:07:58 j-Aspire-5610 gnome-session[1359]: (nautilus:7946): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Dec  6 01:07:58 j-Aspire-5610 gnome-session[1359]: (nautilus:7946): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Dec  6 01:07:58 j-Aspire-5610 gnome-session[1359]: (nautilus:7946): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed


```

---

### Post by matt_symes on 2015-12-06
Hi

> **jj4 said:**
> ```

j@j-Aspire-5610:~$ dmesg | egrep "r852|sdhci"
[    2.562494] sdhci: Secure Digital Host Controller Interface driver
[    2.562498] sdhci: Copyright(c) Pierre Ossman
[    2.570573] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[    2.570606] sdhci-pci 0000:06:04.2: enabling device (0000 -> 0002)
[    2.570736] sdhci-pci 0000:06:04.2: No vmmc regulator found
[    2.570740] sdhci-pci 0000:06:04.2: No vqmmc regulator found
[    2.592147] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[    2.592161] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)
[    2.592305] sdhci-pci 0000:06:04.4: No vmmc regulator found
[    2.592309] sdhci-pci 0000:06:04.4: No vqmmc regulator found
[  470.491316] sdhci: Secure Digital Host Controller Interface driver
[  470.491321] sdhci: Copyright(c) Pierre Ossman
[  470.500738] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[  470.500893] sdhci-pci 0000:06:04.2: No vmmc regulator found
[  470.500898] sdhci-pci 0000:06:04.2: No vqmmc regulator found
[  470.503018] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[  470.503152] sdhci-pci 0000:06:04.4: No vmmc regulator found
[  470.503156] sdhci-pci 0000:06:04.4: No vqmmc regulator found
j@j-Aspire-5610:~$ 


```


No mention of the r852 driver in there. I'm not sure you need it.

> 
ok, now it works on one of the drives but not the other:

```

j@j-Aspire-5610:~$ tail -f /var/log/syslog
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.614516] sdhci: Secure Digital Host Controller Interface driver
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.614521] sdhci: Copyright(c) Pierre Ossman
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.623230] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.625769] sdhci-pci 0000:06:04.2: No vmmc regulator found
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.625776] sdhci-pci 0000:06:04.2: No vqmmc regulator found
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.628659] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.628719] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.628893] sdhci-pci 0000:06:04.4: No vmmc regulator found
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.628897] sdhci-pci 0000:06:04.4: No vqmmc regulator found
Dec  6 01:07:08 j-Aspire-5610 kernel: [33415.630459] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
Dec  6 01:07:46 j-Aspire-5610 kernel: [33453.091240] mmc1: new high speed SDHC card at address 0007
Dec  6 01:07:46 j-Aspire-5610 kernel: [33453.092898] mmcblk0: mmc1:0007 SD32G 28.9 GiB 
Dec  6 01:07:46 j-Aspire-5610 kernel: [33453.095579]  mmcblk0: p1
Dec  6 01:07:46 j-Aspire-5610 udisksd[1562]: Mounted /dev/mmcblk0p1 at /media/j/JPI on behalf of uid 1000
Dec  6 01:07:46 j-Aspire-5610 gnome-session[1359]: (nautilus:7925): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Dec  6 01:07:46 j-Aspire-5610 gnome-session[1359]: (nautilus:7925): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Dec  6 01:07:46 j-Aspire-5610 gnome-session[1359]: (nautilus:7925): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Dec  6 01:07:46 j-Aspire-5610 dbus[597]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Dec  6 01:07:46 j-Aspire-5610 systemd[1]: Starting Hostname Service...
Dec  6 01:07:47 j-Aspire-5610 dbus[597]: [system] Successfully activated service 'org.freedesktop.hostname1'
Dec  6 01:07:47 j-Aspire-5610 systemd[1]: Started Hostname Service.
Dec  6 01:07:50 j-Aspire-5610 kernel: [33457.692148] mmc1: card 0007 removed
Dec  6 01:07:50 j-Aspire-5610 udisksd[1562]: Cleaning up mount point /media/j/JPI (device 179:1 no longer exist)
Dec  6 01:07:50 j-Aspire-5610 systemd[1]: Unmounting /media/j/JPI...
Dec  6 01:07:50 j-Aspire-5610 umount[7937]: umount: /media/j/JPI: not mounted
Dec  6 01:07:50 j-Aspire-5610 systemd[1]: media-j-JPI.mount mount process exited, code=exited status=32
Dec  6 01:07:50 j-Aspire-5610 systemd[1]: Unmounted /media/j/JPI.
Dec  6 01:07:50 j-Aspire-5610 systemd[1]: Unit media-j-JPI.mount entered failed state.
Dec  6 01:07:50 j-Aspire-5610 kernel: [33457.744257] FAT-fs (mmcblk0p1): unable to read boot sector to mark fs as dirty
[B]Dec  6 01:07:57 j-Aspire-5610 kernel: [33465.051216] mmc1: new high speed SDHC card at address 0007
Dec  6 01:07:57 j-Aspire-5610 kernel: [33465.051492] mmcblk0: mmc1:0007 SD32G 28.9 GiB[/B] 
Dec  6 01:07:57 j-Aspire-5610 kernel: [33465.053931]  mmcblk0: p1
Dec  6 01:07:58 j-Aspire-5610 systemd[1]: media-j-JPI.mount failed to run 'mount' task: No such file or directory
Dec  6 01:07:58 j-Aspire-5610 systemd[1]: Failed to mount /media/j/JPI.
Dec  6 01:07:58 j-Aspire-5610 systemd[1]: Mounting /media/j/JPI...
**Dec  6 01:07:58 j-Aspire-5610 kernel: [33465.608461] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.**
**Dec  6 01:07:58 j-Aspire-5610 udisksd[1562]: Mounted /dev/mmcblk0p1 at /media/j/JPI1 on behalf of uid 1000**
Dec  6 01:07:58 j-Aspire-5610 gnome-session[1359]: (nautilus:7946): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Dec  6 01:07:58 j-Aspire-5610 gnome-session[1359]: (nautilus:7946): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Dec  6 01:07:58 j-Aspire-5610 gnome-session[1359]: (nautilus:7946): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed


```

It looks to be finding the card as I highlighted in bold above. The above entry in bold above does suggest it's mounting it under /media/j/JPI1.

It is suggesting you run fsck on the card. The file system on the card looks to be FAT32.

You can run fsck.fat to repair it. These are the options.

```
matthew-xu-16-04:/lib/udev:2 % fsck.fat       
usage: fsck.fat [-aAbflrtvVwy] [-d path -d ...] [-u path -u ...]
               device
  -a       automatically repair the filesystem
  -A       toggle Atari filesystem format
  -b       make read-only boot sector check
  -c N     use DOS codepage N to decode short file names (default: 437)
  -d path  drop that file
  -f       salvage unused chains to files
  -l       list path names
  -n       no-op, check non-interactively without changing
  -p       same as -a, for compat with other *fsck
  -r       interactively repair the filesystem (default)
  -t       test for bad clusters
  -u path  try to undelete that (non-directory) file
  -v       verbose mode
  -V       perform a verification pass
  -w       write changes to disk immediately
  -y       same as -a, for compat with other *fsck
matthew-xu-16-04:/lib/udev:2 % 
```

I would look at running something like this on the card but you'll want to check the options yourself.

```
sudo fsck.fat -a -r -v -w /dev/mmcblk0p1
```

Kind regards

---

### Post by jj4 on 2015-12-06
OK, all working now!

Lastly, I want to clone this device. It has osmc on it so I think I only need the osmc partition but there seem to be a boot and a recovery partition also.
What's the best way to clone it to a new card?  Disk mmcblk0

```

j@j-Aspire-5610:~$ sudo parted -ls
Model: ATA WDC WD2500BEVS-2 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  73.4GB  73.4GB  primary  ntfs         boot
 2      73.4GB  147GB   73.4GB  primary  ntfs
 3      147GB   250GB   103GB   primary  ext4


Model: SD 00000 (sd/mmc)
Disk /dev/mmcblk0: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  124MB   123MB   primary   fat16        lba
 2      126MB   15.7GB  15.6GB  extended
 5      130MB   214MB   83.9MB  logical   fat32        lba
 6      218MB   15.7GB  15.5GB  logical   ext4
 3      15.7GB  15.7GB  33.6MB  primary   ext4


j@j-Aspire-5610:~$ sudo lsblk -fm
NAME        FSTYPE LABEL     UUID                                 MOUNTPOINT                NAME          SIZE OWNER GROUP MODE
sda                                                                                         sda         232.9G root  disk  brw-rw----
&#9500;&#9472;sda1      ntfs             5D34D268177B47F4                     /media/j/5D34D268177B47F4 &#9500;&#9472;sda1       68.4G root  disk  brw-rw----
&#9500;&#9472;sda2      ntfs   Trading   39B76B7A421D646B                                               &#9500;&#9472;sda2       68.4G root  disk  brw-rw----
&#9492;&#9472;sda3      ext4             bd206689-5478-43d0-bc8d-e91c05514cde /                         &#9492;&#9472;sda3       96.2G root  disk  brw-rw----
sr0                                                                                         sr0          1024M root  cdrom brw-rw----
mmcblk0                                                                                     mmcblk0      14.7G root  disk  brw-rw----
&#9500;&#9472;mmcblk0p1 vfat   RECOVERY  5841-0A00                                                      &#9500;&#9472;mmcblk0p1 117.3M root  disk  brw-rw----
&#9500;&#9472;mmcblk0p3 ext4   SETTINGS  15480a7d-4b87-4d4b-a4ca-93331c58d0f8 /media/j/SETTINGS         &#9500;&#9472;mmcblk0p3    32M root  disk  brw-rw----
&#9500;&#9472;mmcblk0p5 vfat   boot-rbp1 0235-7A1F                            /media/j/boot-rbp1        &#9500;&#9472;mmcblk0p5    80M root  disk  brw-rw----
&#9492;&#9472;mmcblk0p6 ext4   root-rbp1 03c61396-b41f-4233-b70e-5d285cee047a /media/j/root-rbp1        &#9492;&#9472;mmcblk0p6  14.4G root  disk  brw-rw----
j@j-Aspire-5610:~$ 


```

---

### Post by matt_symes on 2015-12-06
Hi

You can use ddrescue to image the card or a partition on the card.

```
sudo apt-get install gddrescue
```

```
sudo ddrescue /dev/mmcblk0 ~/card_backup.img
```

The last command above will backup the entire card to the file card_backup.img in your home directory (16G in size).

If you just want a partition then use *mmcblk0pX* where X is the partition number.

If this fixes this for you then please post back to say so and also mark the thread as SOLVED.

**EDIT:**

When you need to restore the image you would use something along the lines of...

```
sudo ddrescue **--force** ~/card_backup.img /dev/mmcblk0
```

**EDIT2:**

I forgot to ask, are your SD cards still recognised after a reboot ?

Kind regards

---

