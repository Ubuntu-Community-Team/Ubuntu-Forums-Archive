---
title: "Ubuntu 16.04 does not recognise external hard disk drive"
date: 2017-07-15
forum: General Help
---

### Post by AnupamMitra on 2017-07-15
I'm having Seagate 1 TB External Hard Disk. As this was not recognised, I tried *sudo fdisk -l *in terminal and output is as under.

```
anupam@anupam:~$ sudo fdisk -l
[sudo] password for anupam: 
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x5ab9f0b2

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048 1936984063 1936982016 923.6G 83 Linux
/dev/sda2       1936986110 1953523711   16537602   7.9G  5 Extended
/dev/sda5       1936986112 1953523711   16537600   7.9G 82 Linux swap / Solaris

Partition 2 does not start on physical sector boundary.
```

Then I tried *dmesg | tail -n 20* and the output is as under.

```
anupam@anupam:~$ dmesg | tail -n 20
[ 1347.430433] blk_update_request: I/O error, dev sdb, sector 5971895
[ 1347.430437] Buffer I/O error on dev sdb1, logical block 5971832, lost async page write
[ 1347.430439] Buffer I/O error on dev sdb1, logical block 5971833, lost async page write
[ 1347.430440] Buffer I/O error on dev sdb1, logical block 5971834, lost async page write
[ 1347.430442] Buffer I/O error on dev sdb1, logical block 5971835, lost async page write
[ 1347.430443] Buffer I/O error on dev sdb1, logical block 5971836, lost async page write
[ 1347.430445] Buffer I/O error on dev sdb1, logical block 5971837, lost async page write
[ 1347.430446] Buffer I/O error on dev sdb1, logical block 5971838, lost async page write
[ 1347.430448] Buffer I/O error on dev sdb1, logical block 5971839, lost async page write
[ 1347.430450] Buffer I/O error on dev sdb1, logical block 5971840, lost async page write
[ 1347.430452] Buffer I/O error on dev sdb1, logical block 5971841, lost async page write
[ 1347.437595] sd 4:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1347.437599] sd 4:0:0:0: [sdb] tag#0 CDB: Write(10) 2a 00 00 5b 20 a7 00 00 f0 00
[ 1347.437601] blk_update_request: I/O error, dev sdb, sector 5972135
[ 1347.478594] blk_update_request: I/O error, dev sdb, sector 0
[ 1347.486487] sd 4:0:0:0: [sdb] Synchronizing SCSI cache
[ 1347.486513] sd 4:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1497.702987] vboxdrv: 00000000 VMMR0.r0
[ 1497.824184] vboxdrv: 00000000 VBoxDDR0.r0
[ 1497.851819] vboxdrv: 00000000 VBoxEhciR0.r0
```


The commands were run when the External H/D was connected in the USB port of the CPU.

---

### Post by ajgreeny on 2017-07-15
Following from the final 3 lines of the **dmesg | tail** output can you please confirm that the OS you are using is not actually a VM running in VBox.

If it is a VM it could be a USB problem of the VM itself, and nothing to do with the external disk.

---

### Post by AnupamMitra on 2017-07-16
> **ajgreeny said:**
> Following from the final 3 lines of the **dmesg | tail** output can you please confirm that the OS you are using is not actually a VM running in VBox.

If it is a VM it could be a USB problem of the VM itself, and nothing to do with the external disk.

Sorry for the delay in giving reply. I let you know that OS is Ubuntu 16.04 and not VM running in VBox. However, in Ubuntu 16.04, Oracle VM Virtual Box has been installed.

---

### Post by vasa1 on 2017-07-16
Install *inxi* and then run *inxi -F* for people to get an idea of your system.

---

### Post by BenginM on 2017-07-16
Salutations!

can get some more info from your logs...

Open a terminal and type

tail -f /var/log/syslog

Plug the drive into a different USB port and wait for 20 seconds and post the entire output

after the drive has settled down can you also post the output of

sudo parted -l

and finally this with the drive attached and settled.

sudo lshw -C storage

sudo lsusb -t

---

### Post by AnupamMitra on 2017-07-22
> **BenginM said:**
> Salutations!

can get some more info from your logs...

Open a terminal and type

tail -f /var/log/syslog

Plug the drive into a different USB port and wait for 20 seconds and post the entire output

after the drive has settled down can you also post the output of

sudo parted -l

and finally this with the drive attached and settled.

sudo lshw -C storage

sudo lsusb -t

As I was out of station, could not provide you the desired information in time, which I regret.

```

anupam@anupam:~$ tail -f /var/log/syslog
Jul 22 13:39:34 anupam ntfs-3g[2208]: Unmounting /dev/sdb1 (Expansion Drive)
Jul 22 13:39:34 anupam udisksd[1915]: Unmounted /dev/sdb1 on behalf of uid 1000
Jul 22 13:39:34 anupam udisksd[1915]: Successfully sent SCSI command SYNCHRONIZE CACHE to /dev/sdb
Jul 22 13:39:35 anupam udisksd[1915]: Successfully sent SCSI command START STOP UNIT to /dev/sdb
Jul 22 13:39:36 anupam gnome-session[1728]: (nautilus:1888): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed
Jul 22 13:39:38 anupam kernel: [  196.225993] sd 4:0:0:0: [sdb] Synchronizing SCSI cache
Jul 22 13:39:36 anupam gnome-session[1728]: message repeated 5 times: [ (nautilus:1888): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed]
Jul 22 13:39:38 anupam udisksd[1915]: Powered off /dev/sdb - successfully wrote to sysfs path /sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/remove
Jul 22 13:39:38 anupam kernel: [  196.272660] usb 1-10: USB disconnect, device number 4
Jul 22 13:39:42 anupam colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jul 22 13:40:42 anupam kernel: [  260.603996] usb 1-10: new high-speed USB device number 5 using xhci_hcd
Jul 22 13:40:42 anupam kernel: [  260.733218] usb 1-10: New USB device found, idVendor=0bc2, idProduct=2300
Jul 22 13:40:42 anupam kernel: [  260.733227] usb 1-10: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 22 13:40:42 anupam kernel: [  260.733233] usb 1-10: Product: Portable        
Jul 22 13:40:42 anupam kernel: [  260.733238] usb 1-10: Manufacturer: Seagate 
Jul 22 13:40:42 anupam kernel: [  260.733242] usb 1-10: SerialNumber: 2GHXPHDM    
Jul 22 13:40:42 anupam kernel: [  260.733984] usb-storage 1-10:1.0: USB Mass Storage device detected
Jul 22 13:40:42 anupam kernel: [  260.734195] usb-storage 1-10:1.0: Quirks match for vid 0bc2 pid 2300: 200000
Jul 22 13:40:42 anupam kernel: [  260.734323] scsi host5: usb-storage 1-10:1.0
Jul 22 13:40:42 anupam mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-10"
Jul 22 13:40:42 anupam mtp-probe: bus: 1, device: 5 was not an MTP device
Jul 22 13:40:43 anupam kernel: [  261.732623] scsi 5:0:0:0: Direct-Access     Seagate  Portable         0130 PQ: 0 ANSI: 4
Jul 22 13:40:43 anupam kernel: [  261.733446] sd 5:0:0:0: Attached scsi generic sg2 type 0
Jul 22 13:40:43 anupam kernel: [  261.733488] sd 5:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
Jul 22 13:40:43 anupam kernel: [  261.733807] sd 5:0:0:0: [sdb] Write Protect is off
Jul 22 13:40:43 anupam kernel: [  261.733814] sd 5:0:0:0: [sdb] Mode Sense: 2f 08 00 00
Jul 22 13:40:43 anupam kernel: [  261.734131] sd 5:0:0:0: [sdb] No Caching mode page found
Jul 22 13:40:43 anupam kernel: [  261.734136] sd 5:0:0:0: [sdb] Assuming drive cache: write back
Jul 22 13:40:43 anupam kernel: [  261.774341]  sdb: sdb1
Jul 22 13:40:43 anupam kernel: [  261.775724] sd 5:0:0:0: [sdb] Attached SCSI disk
Jul 22 13:40:44 anupam kernel: [  262.075725] sd 5:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Jul 22 13:40:44 anupam kernel: [  262.075741] sd 5:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Jul 22 13:40:44 anupam kernel: [  262.075751] sd 5:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
Jul 22 13:40:44 anupam kernel: [  262.075762] sd 5:0:0:0: [sdb] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00
Jul 22 13:40:44 anupam kernel: [  262.232898] sd 5:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Jul 22 13:40:44 anupam kernel: [  262.232910] sd 5:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Jul 22 13:40:44 anupam kernel: [  262.232916] sd 5:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
Jul 22 13:40:44 anupam kernel: [  262.232923] sd 5:0:0:0: [sdb] tag#0 CDB: ATA command pass through(12)/Blank a1 06 20 da 00 00 4f c2 00 b0 00 00
Jul 22 13:40:45 anupam udisksd[1915]: Mounted /dev/sdb1 at /media/anupam/Expansion Drive on behalf of uid 1000
Jul 22 13:40:45 anupam ntfs-3g[2577]: Version 2015.3.14AR.1 integrated FUSE 28
Jul 22 13:40:45 anupam ntfs-3g[2577]: Mounted /dev/sdb1 (Read-Write, label "Expansion Drive", NTFS 3.1)
Jul 22 13:40:45 anupam ntfs-3g[2577]: Cmdline options: rw,nodev,nosuid,uid=1000,gid=1000,uhelper=udisks2
Jul 22 13:40:45 anupam ntfs-3g[2577]: Mount options: rw,nodev,nosuid,uhelper=udisks2,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdb1,blkdev,blksize=4096
Jul 22 13:40:45 anupam ntfs-3g[2577]: Global ownership and permissions enforced, configuration type 7
Jul 22 13:40:45 anupam gnome-session[1728]: (nautilus:2579): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Jul 22 13:40:45 anupam gnome-session[1728]: (nautilus:2579): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Jul 22 13:40:45 anupam gnome-session[1728]: (nautilus:2579): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Jul 22 13:40:45 anupam gnome-session[1728]: (nautilus:2579): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Jul 22 13:40:45 anupam gnome-session[1728]: (nautilus:2579): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Jul 22 13:40:45 anupam dbus[749]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jul 22 13:40:45 anupam systemd[1]: Starting Hostname Service...
Jul 22 13:40:45 anupam dbus[749]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul 22 13:40:45 anupam systemd[1]: Started Hostname Service.
Jul 22 13:40:46 anupam colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1


```

In the midway, suddenly my external hard disk appeared in Launcher. 
However, the outcome of *sudo parted -l* is as under.

```

sudo parted -l
Jul 22 13:47:02 anupam kernel: [  640.787338] sd 5:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Jul 22 13:47:02 anupam kernel: [  640.787355] sd 5:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Jul 22 13:47:02 anupam kernel: [  640.787364] sd 5:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
Jul 22 13:47:02 anupam kernel: [  640.787374] sd 5:0:0:0: [sdb] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00
Jul 22 13:48:52 anupam systemd[1]: Started CUPS Scheduler.
Jul 22 13:48:52 anupam colord[956]: (colord:956): Cd-WARNING **: failed to get session [pid 2693]: No such device or address
Jul 22 13:51:50 anupam systemd[1]: Starting Cleanup of Temporary Directories...
Jul 22 13:51:50 anupam systemd-tmpfiles[2766]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Jul 22 13:51:50 anupam systemd[1]: Started Cleanup of Temporary Directories.
Jul 22 13:57:02 anupam kernel: [ 1240.715602] sd 5:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Jul 22 13:57:02 anupam kernel: [ 1240.715613] sd 5:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Jul 22 13:57:02 anupam kernel: [ 1240.715619] sd 5:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
Jul 22 13:57:02 anupam kernel: [ 1240.715627] sd 5:0:0:0: [sdb] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00

```

Outcome of *sudo lshw -C storage* is as under.
```

sudo lshw -C storage

Jul 22 14:01:53 anupam systemd[1]: Started CUPS Scheduler.
Jul 22 14:01:53 anupam colord[956]: (colord:956): Cd-WARNING **: failed to get session [pid 2801]: No such device or address

```

Lastly, [I]sudo lsusb -t
[/I]```

sudo lsusb -tJul 22 14:07:02 anupam kernel: [ 1840.729423] sd 5:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Jul 22 14:07:02 anupam kernel: [ 1840.729434] sd 5:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Jul 22 14:07:02 anupam kernel: [ 1840.729440] sd 5:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
Jul 22 14:07:02 anupam kernel: [ 1840.729448] sd 5:0:0:0: [sdb] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00
Jul 22 14:08:22 anupam gnome-session[1728]: <gettext.GNUTranslations object at 0xb3194d8c>
Jul 22 14:08:22 anupam gnome-session[1728]: #####################################################
Jul 22 14:08:22 anupam gnome-session[1728]: System: Linux
Jul 22 14:08:22 anupam gnome-session[1728]: Machine: i686
Jul 22 14:08:22 anupam gnome-session[1728]: Node: anupam
Jul 22 14:08:22 anupam gnome-session[1728]: Release: 4.4.0-83-generic
Jul 22 14:08:22 anupam gnome-session[1728]: Version: #106-Ubuntu SMP Mon Jun 26 17:54:25 UTC 2017
Jul 22 14:08:22 anupam gnome-session[1728]: Platform: Linux-4.4.0-83-generic-i686-with-Ubuntu-16.04-xenial
Jul 22 14:08:22 anupam gnome-session[1728]: My-Weather-Indicator version: 0.8.1-0extras16.04.1
Jul 22 14:08:22 anupam gnome-session[1728]: #####################################################
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Requesting timezone identificacion
Jul 22 14:08:22 anupam gnome-session[1728]: ** OWM **
Jul 22 14:08:22 anupam gnome-session[1728]: 1277780 88.3247 22.785
Jul 22 14:08:22 anupam gnome-session[1728]: 1
Jul 22 14:08:22 anupam gnome-session[1728]: ***** refreshing weather *****
Jul 22 14:08:22 anupam gnome-session[1728]: <urlopen error unknown url type: https>
Jul 22 14:08:22 anupam gnome-session[1728]: --- Updating data in location 0 ---
Jul 22 14:08:22 anupam gnome-session[1728]: ******* Adquiring inv direction *******
Jul 22 14:08:22 anupam gnome-session[1728]: 0.0 0.0
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Requesting timezone identificacion
Jul 22 14:08:22 anupam gnome-session[1728]: ** OWM **
Jul 22 14:08:22 anupam gnome-session[1728]: 6295630 0.0 0.0
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Updating weather
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Calculating rawOffset
Jul 22 14:08:22 anupam gnome-session[1728]: -------------------------------------------------------
Jul 22 14:08:22 anupam gnome-session[1728]: OpenWeatherMap Weather Service url:http://api.openweathermap.org/data/2.5/weather?id=6295630&appid=4516154e5c8a6494e7e13b550408c863
Jul 22 14:08:22 anupam gnome-session[1728]: -------------------------------------------------------
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Updated weather
Jul 22 14:08:22 anupam gnome-session[1728]: None
Jul 22 14:08:22 anupam gnome-session[1728]: --- End of updating data in location 0 ---
Jul 22 14:08:22 anupam gnome-session[1728]: *** Looking For Internet ***
Jul 22 14:08:22 anupam gnome-session[1728]: <urlopen error unknown url type: https>
Jul 22 14:08:22 anupam gnome-session[1728]: *** Internet Found ***
Jul 22 14:08:22 anupam gnome-session[1728]: ***** refreshing weather *****
Jul 22 14:08:22 anupam gnome-session[1728]: <urlopen error unknown url type: https>
Jul 22 14:08:22 anupam gnome-session[1728]: --- Updating data in location 0 ---
Jul 22 14:08:22 anupam gnome-session[1728]: ******* Adquiring inv direction *******
Jul 22 14:08:22 anupam gnome-session[1728]: 22.8692 88.3772 Chandannagar
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Requesting timezone identificacion
Jul 22 14:08:22 anupam gnome-session[1728]: ** OWM **
Jul 22 14:08:22 anupam gnome-session[1728]: 1274784 88.3772 22.8692
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Updating weather
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Calculating rawOffset
Jul 22 14:08:22 anupam gnome-session[1728]: -------------------------------------------------------
Jul 22 14:08:22 anupam gnome-session[1728]: OpenWeatherMap Weather Service url:http://api.openweathermap.org/data/2.5/weather?id=1274784&appid=4516154e5c8a6494e7e13b550408c863
Jul 22 14:08:22 anupam gnome-session[1728]: -------------------------------------------------------
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Updated weather
Jul 22 14:08:22 anupam gnome-session[1728]: {'current_conditions': {'dusk': '19:32', 'condition': 'partly cloudy', 'condition_text': 'Partly cloudy', 'dawn_time': '06:41', 'solarradiation': None, 'condition_icon_dark': 'mwid-partly-cloudy.png', 'rawOffset': 1.0, 'visibility': None, 'sunrise': '07:03', 'dawn': '06:41', 'moon_icon': 'mwi-moon27.png', 'dew_point': '23', 'cloudiness': '44 %', 'feels_like': '23', 'UV': None, 'dusk_time': '19:32', 'sunrise_time': '07:03', 'pressure': '1031 millibar', 'windchill': 0.0, 'sunset_time_utc': '18:10', 'sunset_time': '19:10', 'heat_index': 0, 'precip_1hr': None, 'temperature': '23', 'humidity': '100 %', 'condition_icon_light': 'mwil-partly-cloudy.png', 'isday': True, 'wind_icon': 'mwi-wind17.png', 'precip_today': None, 'sunset': '19:10', 'condition_image': 'mwig-partly-cloudy.png', 'sunrise_time_utc': '06:03', 'moon_phase': 'New Moon', 'wind_condition': '6 km/h (SBW)'}, 'ok': True, 'forecasts': [{'condition': 'partly sunny', 'condition_text': 'Partly sunny', 'qpf_allday': None, 'sunrise': '07:03', 'snow_night': None, 'moon_icon': 'mwi-moon27.png', 'snow_day': None, 'cloudiness': '12 %', 'sunset': '19:10', 'day_of_week': 'Saturday', 'avewind': '5 km/h (SBW)', 'condition_image': 'mwig-partly-cloudy.png', 'moon_phase': 'New Moon', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '100 %', 'qpf_night': None, 'low': '22', 'wind_icon': 'mwi-wind17.png', 'qpf_day': None, 'high': '23', 'condition_icon': 'mwil-partly-cloudy.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'light rain', 'condition_text': 'Rain', 'qpf_allday': None, 'sunrise': '07:03', 'snow_night': None, 'moon_icon': 'mwi-moon28.png', 'snow_day': None, 'cloudiness': '80 %', 'sunset': '19:10', 'day_of_week': 'Sunday', 'avewind': '6 km/h (S)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'New Moon', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '100 %', 'qpf_night': None, 'low': '22', 'wind_icon': 'mwi-wind16.png', 'qpf_day': None, 'high': '23', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}, {'condition':
Jul 22 14:08:22 anupam gnome-session[1728]:  'partly cloudy', 'condition_text': 'Partly cloudy', 'qpf_allday': None, 'sunrise': '07:03', 'snow_night': None, 'moon_icon': 'mwi-moon01.png', 'snow_day': None, 'cloudiness': '48 %', 'sunset': '19:10', 'day_of_week': 'Monday', 'avewind': '8 km/h (S)', 'condition_image': 'mwig-partly-cloudy.png', 'moon_phase': 'New Moon', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '100 %', 'qpf_night': None, 'low': '22', 'wind_icon': 'mwi-wind16.png', 'qpf_day': None, 'high': '23', 'condition_icon': 'mwil-partly-cloudy.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'light rain', 'condition_text': 'Rain', 'qpf_allday': None, 'sunrise': '07:03', 'snow_night': None, 'moon_icon': 'mwi-moon02.png', 'snow_day': None, 'cloudiness': '35 %', 'sunset': '19:10', 'day_of_week': 'Tuesday', 'avewind': '7 km/h (SBE)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'New Moon', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '0 %', 'qpf_night': None, 'low': '22', 'wind_icon': 'mwi-wind15.png', 'qpf_day': None, 'high': '23', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'light rain', 'condition_text': 'Rain', 'qpf_allday': None, 'sunrise': '07:03', 'snow_night': None, 'moon_icon': 'mwi-moon03.png', 'snow_day': None, 'cloudiness': '26 %', 'sunset': '19:10', 'day_of_week': 'Wednesday', 'avewind': '6 km/h (SSE)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'Waxing Crescent', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '0 %', 'qpf_night': None, 'low': '22', 'wind_icon': 'mwi-wind14.png', 'qpf_day': None, 'high': '22', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'light rain', 'condition_text': 'Rain', 'qpf_allday': None, 'sunrise': '07:03', 'snow_night': None, 'moon_icon': 'mwi-moon04.png', 'snow_day': None, 'cloudiness': '40 %', 'sunset': '19:10', 'day_of_week': 'Thursday', 'avewind': '8 km/h (SSE)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'Waxing Crescent', 'maxhumidity': None, 'minhumidity': None, '
Jul 22 14:08:22 anupam gnome-session[1728]: avehumidity': '0 %', 'qpf_night': None, 'low': '23', 'wind_icon': 'mwi-wind14.png', 'qpf_day': None, 'high': '23', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'light rain', 'condition_text': 'Rain', 'qpf_allday': None, 'sunrise': '07:03', 'snow_night': None, 'moon_icon': 'mwi-moon05.png', 'snow_day': None, 'cloudiness': '23 %', 'sunset': '19:10', 'day_of_week': 'Friday', 'avewind': '5 km/h (SE)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'Waxing Crescent', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '0 %', 'qpf_night': None, 'low': '23', 'wind_icon': 'mwi-wind12.png', 'qpf_day': None, 'high': '23', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}], 'update_time': 1500710865.1632693, 'forecast_information': {'postal_code': '', 'forecast_date': '', 'current_date_time': '', 'city': '...', 'latitude_e6': '', 'longitude_e6': '', 'unit_system': 'SI'}}
Jul 22 14:08:22 anupam gnome-session[1728]: --- End of updating data in location 0 ---
Jul 22 14:08:22 anupam gnome-session[1728]: ***** refreshing weather *****
Jul 22 14:08:22 anupam gnome-session[1728]: <urlopen error unknown url type: https>
Jul 22 14:08:22 anupam gnome-session[1728]: --- Updating data in location 0 ---
Jul 22 14:08:22 anupam gnome-session[1728]: ******* Adquiring inv direction *******
Jul 22 14:08:22 anupam gnome-session[1728]: 22.8692 88.3772 Chandannagar
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Updating weather
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Calculating rawOffset
Jul 22 14:08:22 anupam gnome-session[1728]: -------------------------------------------------------
Jul 22 14:08:22 anupam gnome-session[1728]: OpenWeatherMap Weather Service url:http://api.openweathermap.org/data/2.5/weather?id=1274784&appid=4516154e5c8a6494e7e13b550408c863
Jul 22 14:08:22 anupam gnome-session[1728]: -------------------------------------------------------
Jul 22 14:08:22 anupam gnome-session[1728]: ****** Updated weather
Jul 22 14:08:22 anupam gnome-session[1728]: {'current_conditions': {'dusk': '18:47', 'condition': 'light rain', 'condition_text': 'Rain', 'dawn_time': '04:39', 'solarradiation': None, 'condition_icon_dark': 'mwid-rain.png', 'rawOffset': 5.5, 'visibility': None, 'sunrise': '05:03', 'dawn': '04:39', 'moon_icon': 'mwi-moon27.png', 'dew_point': '26', 'cloudiness': '90 %', 'feels_like': '31', 'UV': None, 'dusk_time': '18:47', 'sunrise_time': '05:03', 'pressure': '999 millibar', 'windchill': 0.0, 'sunset_time_utc': '12:53', 'sunset_time': '18:23', 'heat_index': 7.495130058399894, 'precip_1hr': None, 'temperature': '27', 'humidity': '94 %', 'condition_icon_light': 'mwil-rain.png', 'isday': True, 'wind_icon': 'mwi-wind04.png', 'precip_today': None, 'sunset': '18:23', 'condition_image': 'mwig-rain.png', 'sunrise_time_utc': '23:33', 'moon_phase': 'New Moon', 'wind_condition': '2 km/h (NE)'}, 'ok': True, 'forecasts': [{'condition': 'heavy intensity rain', 'condition_text': 'Intensity rain', 'qpf_allday': None, 'sunrise': '05:03', 'snow_night': None, 'moon_icon': 'mwi-moon27.png', 'snow_day': None, 'cloudiness': '100 %', 'sunset': '18:23', 'day_of_week': 'Saturday', 'avewind': '4 km/h (W)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'New Moon', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '100 %', 'qpf_night': None, 'low': '25', 'wind_icon': 'mwi-wind24.png', 'qpf_day': None, 'high': '28', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'heavy intensity rain', 'condition_text': 'Intensity rain', 'qpf_allday': None, 'sunrise': '05:04', 'snow_night': None, 'moon_icon': 'mwi-moon28.png', 'snow_day': None, 'cloudiness': '92 %', 'sunset': '18:22', 'day_of_week': 'Sunday', 'avewind': '7 km/h (SW)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'New Moon', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '95 %', 'qpf_night': None, 'low': '24', 'wind_icon': 'mwi-wind20.png', 'qpf_day': None, 'high': '27', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'heavy intensi
Jul 22 14:08:22 anupam gnome-session[1728]: ty rain', 'condition_text': 'Intensity rain', 'qpf_allday': None, 'sunrise': '05:04', 'snow_night': None, 'moon_icon': 'mwi-moon01.png', 'snow_day': None, 'cloudiness': '92 %', 'sunset': '18:22', 'day_of_week': 'Monday', 'avewind': '6 km/h (SW)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'New Moon', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '98 %', 'qpf_night': None, 'low': '24', 'wind_icon': 'mwi-wind20.png', 'qpf_day': None, 'high': '27', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'heavy intensity rain', 'condition_text': 'Intensity rain', 'qpf_allday': None, 'sunrise': '05:04', 'snow_night': None, 'moon_icon': 'mwi-moon02.png', 'snow_day': None, 'cloudiness': '27 %', 'sunset': '18:22', 'day_of_week': 'Tuesday', 'avewind': '4 km/h (SWBS)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'New Moon', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '0 %', 'qpf_night': None, 'low': '25', 'wind_icon': 'mwi-wind19.png', 'qpf_day': None, 'high': '29', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'moderate rain', 'condition_text': 'Moderate rain', 'qpf_allday': None, 'sunrise': '05:05', 'snow_night': None, 'moon_icon': 'mwi-moon03.png', 'snow_day': None, 'cloudiness': '17 %', 'sunset': '18:21', 'day_of_week': 'Wednesday', 'avewind': '3 km/h (SEBE)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'Waxing Crescent', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '0 %', 'qpf_night': None, 'low': '25', 'wind_icon': 'mwi-wind11.png', 'qpf_day': None, 'high': '30', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'heavy intensity rain', 'condition_text': 'Intensity rain', 'qpf_allday': None, 'sunrise': '05:05', 'snow_night': None, 'moon_icon': 'mwi-moon04.png', 'snow_day': None, 'cloudiness': '25 %', 'sunset': '18:21', 'day_of_week': 'Thursday', 'avewind': '4 km/h (SEBS)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'Waxing Crescent', 'maxhumidity'
Jul 22 14:08:29 anupam gnome-session[1728]: : None, 'minhumidity': None, 'avehumidity': '0 %', 'qpf_night': None, 'low': '26', 'wind_icon': 'mwi-wind13.png', 'qpf_day': None, 'high': '30', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}, {'condition': 'light rain', 'condition_text': 'Rain', 'qpf_allday': None, 'sunrise': '05:06', 'snow_night': None, 'moon_icon': 'mwi-moon05.png', 'snow_day': None, 'cloudiness': '31 %', 'sunset': '18:20', 'day_of_week': 'Friday', 'avewind': '4 km/h (SEBE)', 'condition_image': 'mwig-rain.png', 'moon_phase': 'Waxing Crescent', 'maxhumidity': None, 'minhumidity': None, 'avehumidity': '0 %', 'qpf_night': None, 'low': '25', 'wind_icon': 'mwi-wind11.png', 'qpf_day': None, 'high': '31', 'condition_icon': 'mwil-rain.png', 'maxwind': None, 'snow_allday': None}], 'update_time': 1500710886.8930357, 'forecast_information': {'postal_code': '', 'forecast_date': '', 'current_date_time': '', 'city': '...', 'latitude_e6': '', 'longitude_e6': '', 'unit_system': 'SI'}}
Jul 22 14:08:29 anupam gnome-session[1728]: --- End of updating data in location 0 ---

```I do repeat that my External Harddisk is now visible in Launcher and I can get access into it.
Awaiting for your further advice and valued opinion.

---

