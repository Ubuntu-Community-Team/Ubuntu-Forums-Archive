---
title: "Problem with a disk adapter"
date: 2022-09-28
forum: General Help
---

### Post by georgesgiralt on 2022-09-28
Hello !
I own a little disk adapter (SATA, can do optical drives too) from Icy-Box. It comes with a power supply one can use if your device is energy hungry. It is performing flawlessly under windows (10 and 11) on the very same laptop and USB port giving me trouble. 
When I plug it under Ubuntu, the disk is seen, detected, mounted and then disconnect then discovered again, detected, mounted and so on. The disk goes from sdb, to sdc, sdd.... until I stop it by plugin it out. On the exemple below, the optional power supply is plugged. So no power related problem IMHO.
Here is what I find int the syslog : 

```

 kernel: [55173.605947] usb 4-2: new SuperSpeed USB device number 6 using xhci_hcd
 kernel: [55173.626960] usb 4-2: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
 kernel: [55173.626969] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
 kernel: [55173.626973] usb 4-2: Product: IB-AC704-6G
 kernel: [55173.626975] usb 4-2: Manufacturer: ICY BOX
 kernel: [55173.626977] usb 4-2: SerialNumber: 2017120001C3
 kernel: [55173.628726] usb-storage 4-2:1.0: USB Mass Storage device detected
 kernel: [55173.628997] usb-storage 4-2:1.0: Quirks match for vid 174c pid 55aa: 400000
 kernel: [55173.629039] scsi host3: usb-storage 4-2:1.0
 mtp-probe: checking bus 4, device 6: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-2"
 mtp-probe: bus: 4, device: 6 was not an MTP device
 mtp-probe: checking bus 4, device 6: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-2"
 mtp-probe: bus: 4, device: 6 was not an MTP device
 kernel: [55174.646344] scsi 3:0:0:0: Direct-Access     ICY BOX  IB-AC704-6G      0    PQ: 0 ANSI: 6
 kernel: [55174.646863] sd 3:0:0:0: Attached scsi generic sg2 type 0
 kernel: [55174.647164] sd 3:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
 kernel: [55174.647173] sd 3:0:0:0: [sdc] 4096-byte physical blocks
 kernel: [55174.647552] sd 3:0:0:0: [sdc] Write Protect is off
 kernel: [55174.647560] sd 3:0:0:0: [sdc] Mode Sense: 43 00 00 00
 kernel: [55174.647901] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 kernel: [55174.700766] GPT:Primary header thinks Alt. header is not at the end of the disk.
 kernel: [55174.700769] GPT:3907029163 != 3907029167
 kernel: [55174.700778] GPT:Alternate GPT header not at the end of the disk.
 kernel: [55174.700778] GPT:3907029163 != 3907029167
 kernel: [55174.700779] GPT: Use GNU Parted to correct GPT errors.
 kernel: [55174.700784]  sdc: sdc1 sdc2 sdc3 sdc4
 kernel: [55174.701963] sd 3:0:0:0: [sdc] Attached SCSI disk
 systemd-udevd[46564]: sdc: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/sdc' failed with exit code 1.
 systemd-udevd[46560]: sdc4: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/sdc4' failed with exit code 1.
 systemd[1]: Starting LVM event activation on device 8:36...
 systemd-udevd[46562]: sdc2: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/sdc2' failed with exit code 1.
 systemd-udevd[46564]: sdc1: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/sdc1' failed with exit code 1.
 systemd-udevd[46561]: sdc3: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/sdc3' failed with exit code 1.
 lvm[46639]:   pvscan[46639] PV /dev/sdc4 online, VG Test is complete.
 lvm[46639]:   pvscan[46639] VG Test run autoactivation.
 espineux lvm[46639]:   PVID <PV UUID>  read from /dev/sdc4 last written to /dev/sdd4.
 lvm[46639]:   pvscan[46639] VG Test not using quick activation.
 lvm[46639]:   9 logical volume(s) in volume group "Test" now active
 systemd[1]: Finished LVM event activation on device 8:36.
 kernel: [55175.680019] ntfs3: Unknown parameter 'windows_names'
 ntfs-3g[46644]: Version 2021.8.22 integrated FUSE 28
 ntfs-3g[46644]: Mounted /dev/sdc2 (Read-Write, label "", NTFS 3.1)
 udisksd[1031]: Mounted /dev/sdc2 at /media/georges/69DBB946275FB246 on behalf of uid 1000
 ntfs-3g[46644]: Cmdline options: rw,nodev,nosuid,uid=1000,gid=1000,windows_names,uhelper=udisks2
 ntfs-3g[46644]: Mount options: nodev,nosuid,uhelper=udisks2,allow_other,nonempty,relatime,rw,default_permissions,fsname=/dev/sdc2,blkdev,blksize=4096
 ntfs-3g[46644]: Global ownership and permissions enforced, configuration type 7
 dbus-daemon[5463]: [session uid=1000 pid=5463] Activating service name='org.gnome.Shell.HotplugSniffer' requested by ':1.48' (uid=1000 pid=5926 comm="/usr/bin/gnome-shell " label="unconfined")
 dbus-daemon[5463]: [session uid=1000 pid=5463] Successfully activated service 'org.gnome.Shell.HotplugSniffer'
 kernel: [55189.290065] usb 4-2: USB disconnect, device number 6
 udisksd[1031]: Cleaning up mount point /media/georges/69DBB946275FB246 (device 8:34 no longer exists)
 systemd[1]: Stopping LVM event activation on device 8:36...
 ntfs-3g[46644]: Unmounting /dev/sdc2 ()
 ntfs-3g[46644]: Failed to sync device /dev/sdc2: Erreur d'entrée/sortie
 ntfs-3g[46644]: Failed to close volume /dev/sdc2: Erreur d'entrée/sortie
 systemd[1]: media-georges-69DBB946275FB246.mount: Deactivated successfully.
 systemd[1]: lvm2-pvscan@8:36.service: Deactivated successfully.
 systemd[1]: Stopped LVM event activation on device 8:36.
 kernel: [55189.325986] sd 3:0:0:0: [sdc] Synchronizing SCSI cache
 kernel: [55189.326014] sd 3:0:0:0: [sdc] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
 kernel: [55189.327103] buffer_io_error: 54 callbacks suppressed
 kernel: [55189.327112] Buffer I/O error on dev dm-17, logical block 0, async page read
 kernel: [55189.327130] Buffer I/O error on dev dm-17, logical block 0, async page read
 kernel: [55189.327196] Buffer I/O error on dev dm-17, logical block 0, async page read
 kernel: [55189.327199] Buffer I/O error on dev dm-17, logical block 0, async page read
 kernel: [55189.329621] Buffer I/O error on dev dm-23, logical block 0, async page read
 kernel: [55189.329627] Buffer I/O error on dev dm-23, logical block 0, async page read
 kernel: [55189.329644] Buffer I/O error on dev dm-23, logical block 0, async page read
 kernel: [55189.329646] Buffer I/O error on dev dm-23, logical block 0, async page read
 kernel: [55189.332699] Buffer I/O error on dev dm-18, logical block 0, async page read
 kernel: [55189.332707] Buffer I/O error on dev dm-18, logical block 0, async page read

```

And everything reproduce again if i! let the device plugged. 
As this device works flawlessly on the same hardware/port and disk under a different operating system, I bet it is software related. But I can't find what and where it is failing. This behavior happened under 20.04.3 then 4 LTS and now under 22.04.1 (I hoped the upgrade fixed it)
So all help I can get will be greatly appreciated. 
Thanks a lot in advance for it !
P.S. : GPT complains because the last partition on the disk is an LVM PV and LVM put it's label where GPT thought it was safe to put it's backup... I have not found a way, yet, to correct this permanently. The behavior described above is the same if I use a disk without LVM on it.

---

### Post by &amp;KyT$0P# on 2022-09-28
Does your computer have a USB 3.1 Gen 2 port you could try?
Does your computer have a USB 2.0 port, or do you have a USB 2.0 hub that you can use for this?

If yes to any of the above, does it make a difference?

---

### Post by georgesgiralt on 2022-09-28
Yes the 3.1 Gen 2 ports exists. No it make no difference whatever port I use under Ubuntu or Windows. 
All ports are fine under Windows. 
BTW, the laptop is a Lenovo ThinkBook 15 G2 ITL (20VE). 
I've an unpowered USB 3 hub I can try but no USB 2.0 port or hub avail.

---

### Post by &amp;KyT$0P# on 2022-09-28
Do you have another (preferably non-NTFS) disk you can try instead with this adapter as a test?

---

### Post by georgesgiralt on 2022-09-28
I've tested various disks but can't say if they had an NTFS partition on it. Will search my disk drawer and report back.

---

### Post by georgesgiralt on 2022-09-28
I've found one. A very old one. 
Same behaviour, though....
```

[ 2340.830034] usb 4-2: new SuperSpeed USB device number 9 using xhci_hcd
[ 2340.850522] usb 4-2: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
[ 2340.850533] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 2340.850537] usb 4-2: Product: IB-AC704-6G
[ 2340.850540] usb 4-2: Manufacturer: ICY BOX
[ 2340.850542] usb 4-2: SerialNumber: 2017120001C3
[ 2340.853087] usb-storage 4-2:1.0: USB Mass Storage device detected
[ 2340.853350] usb-storage 4-2:1.0: Quirks match for vid 174c pid 55aa: 400000
[ 2340.853416] scsi host2: usb-storage 4-2:1.0
[ 2341.870720] scsi 2:0:0:0: Direct-Access     ICY BOX  IB-AC704-6G      0    PQ: 0 ANSI: 6
[ 2341.871271] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 2341.871468] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/233 GiB)
[ 2341.871761] sd 2:0:0:0: [sdb] Write Protect is off
[ 2341.871765] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 2341.872049] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2341.970446]  sdb: sdb1
[ 2341.996464] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 2343.081777] EXT4-fs (sdb1): mounting ext3 file system using the ext4 subsystem
[ 2343.089784] EXT4-fs (sdb1): warning: checktime reached, running e2fsck is recommended
[ 2343.256071] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
[ 2454.891108] usb 4-2: USB disconnect, device number 9
[ 2454.891366] sd 2:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK cmd_age=0s
[ 2454.891373] sd 2:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 15 a5 a7 8f 00 00 08 00
[ 2454.891375] blk_update_request: I/O error, dev sdb, sector 363177871 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 0
[ 2454.891519] blk_update_request: I/O error, dev sdb, sector 363177871 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2454.891532] Buffer I/O error on dev sdb1, logical block 181588904, async page read
[ 2454.891551] blk_update_request: I/O error, dev sdb, sector 363177873 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2454.891556] Buffer I/O error on dev sdb1, logical block 181588905, async page read
[ 2454.891567] blk_update_request: I/O error, dev sdb, sector 363177875 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2454.891571] Buffer I/O error on dev sdb1, logical block 181588906, async page read
[ 2454.891584] blk_update_request: I/O error, dev sdb, sector 363177877 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2454.891588] Buffer I/O error on dev sdb1, logical block 181588907, async page read
[ 2454.891619] blk_update_request: I/O error, dev sdb, sector 363177871 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2454.891623] Buffer I/O error on dev sdb1, logical block 181588904, async page read
[ 2454.891632] blk_update_request: I/O error, dev sdb, sector 363177873 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2454.891637] Buffer I/O error on dev sdb1, logical block 181588905, async page read
[ 2454.891646] blk_update_request: I/O error, dev sdb, sector 363177875 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2454.891650] Buffer I/O error on dev sdb1, logical block 181588906, async page read
[ 2454.891660] blk_update_request: I/O error, dev sdb, sector 363177877 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2454.891663] Buffer I/O error on dev sdb1, logical block 181588907, async page read
[ 2454.902416] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
[ 2454.902437] sd 2:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 2455.219158] usb 4-2: new SuperSpeed USB device number 10 using xhci_hcd
[ 2455.239818] usb 4-2: New USB device found, idVendor=174c, idProduct=55aa, bcdDevice= 1.00
[ 2455.239828] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 2455.239832] usb 4-2: Product: IB-AC704-6G
[ 2455.239835] usb 4-2: Manufacturer: ICY BOX
[ 2455.239837] usb 4-2: SerialNumber: 2017120001C3
[ 2455.241266] usb-storage 4-2:1.0: USB Mass Storage device detected
[ 2455.241600] usb-storage 4-2:1.0: Quirks match for vid 174c pid 55aa: 400000
[ 2455.241735] scsi host3: usb-storage 4-2:1.0
[ 2456.271455] scsi 3:0:0:0: Direct-Access     ICY BOX  IB-AC704-6G      0    PQ: 0 ANSI: 6
[ 2456.272005] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 2456.272359] sd 3:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/233 GiB)
[ 2456.272665] sd 3:0:0:0: [sdc] Write Protect is off
[ 2456.272677] sd 3:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 2456.272982] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2456.342618]  sdc: sdc1
[ 2456.377079] sd 3:0:0:0: [sdc] Attached SCSI disk
[ 2457.342827] EXT4-fs (sdc1): mounting ext3 file system using the ext4 subsystem
[ 2457.361950] EXT4-fs (sdc1): warning: checktime reached, running e2fsck is recommended
[ 2457.594538] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.

```
N.B. : the device is plugged on a USB SuperSpeed plug with a "plain" usb plug (a blue one on the cable).

---

### Post by corporate-khwilliamson on 2022-10-10
I was getting similar problems.  But I didn't care what was on the disk, as it is just a backup copy of my active disk, and gparted did see the device.  I reformatted it to ext4 (which it was already), and was then able to mount it, and use it.   But my normal incremental backup becomes a full backup

I have another backup disk that worked a couple weeks ago, and it is exhibiting the same issue.  The only change I can think of is that in the meantime I added an extra SSD, so the disk is now sdc1 and not sdb1.  After I've verified I don't really need what is on it, I'll probably wipe it too.

---

