---
title: "How to force mount e-reader"
date: 2021-01-15
forum: General Help
---

### Post by jwoodruff on 2021-01-15
Ubuntu 20.04 on Desktop
I'm hoping someone can help me with trouble mounting my Kobo Vox e-reader on Ubuntu. It doesn't auto mount when connecting by usb.

Output from terminal command "tail -f /var/log/syslog":

Jan 15 11:53:14 BasementDesktop tracker-extract[4537]: Set scheduler policy to SCHED_IDLE
Jan 15 11:53:14 BasementDesktop tracker-extract[4537]: Setting priority nice level to 19
Jan 15 11:53:14 BasementDesktop dbus-daemon[1567]: [session uid=1000 pid=1567] Successfully activated service 'org.freedesktop.Tracker1.Miner.Extract'
Jan 15 11:53:14 BasementDesktop systemd[1557]: Started Tracker metadata extractor.
Jan 15 11:53:14 BasementDesktop kernel: [ 1960.496045] usb 1-7: new high-speed USB device number 10 using ehci-pci
Jan 15 11:53:14 BasementDesktop kernel: [ 1960.662185] usb 1-7: New USB device found, idVendor=2237, idProduct=2208, bcdDevice= 2.26
Jan 15 11:53:14 BasementDesktop kernel: [ 1960.662194] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan 15 11:53:14 BasementDesktop kernel: [ 1960.662198] usb 1-7: Product: Kobo Vox
Jan 15 11:53:14 BasementDesktop kernel: [ 1960.662202] usb 1-7: Manufacturer: Kobo Inc.
Jan 15 11:53:14 BasementDesktop kernel: [ 1960.662206] usb 1-7: SerialNumber: K080W23202DA6
Jan 15 11:53:14 BasementDesktop kernel: [ 1960.667756] usb-storage 1-7:1.0: USB Mass Storage device detected
Jan 15 11:53:14 BasementDesktop kernel: [ 1960.668917] scsi host7: usb-storage 1-7:1.0
Jan 15 11:53:14 BasementDesktop mtp-probe: checking bus 1, device 10: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-7"
Jan 15 11:53:14 BasementDesktop mtp-probe: bus: 1, device: 10 was not an MTP device
Jan 15 11:53:15 BasementDesktop mtp-probe: checking bus 1, device 10: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-7"
Jan 15 11:53:15 BasementDesktop mtp-probe: bus: 1, device: 10 was not an MTP device
Jan 15 11:53:15 BasementDesktop kernel: [ 1961.697375] scsi 7:0:0:0: Direct-Access     Kobo Inc .Kobo Vox         010 PQ: 0 ANSI: 2
Jan 15 11:53:15 BasementDesktop kernel: [ 1961.699387] scsi 7:0:0:1: Direct-Access     Kobo Inc .Kobo Vox         010 PQ: 0 ANSI: 2
Jan 15 11:53:16 BasementDesktop kernel: [ 1961.701304] scsi 7:0:0:2: Direct-Access     Kobo Inc .Kobo Vox         010 PQ: 0 ANSI: 2
Jan 15 11:53:16 BasementDesktop kernel: [ 1961.702133] sd 7:0:0:0: Attached scsi generic sg4 type 0
Jan 15 11:53:16 BasementDesktop kernel: [ 1961.705043] sd 7:0:0:0: Power-on or device reset occurred
Jan 15 11:53:16 BasementDesktop kernel: [ 1961.712067] sd 7:0:0:1: Attached scsi generic sg5 type 0
Jan 15 11:53:16 BasementDesktop kernel: [ 1961.713318] sd 7:0:0:2: Attached scsi generic sg6 type 0
Jan 15 11:53:16 BasementDesktop kernel: [ 1961.714379] sd 7:0:0:1: Power-on or device reset occurred
Jan 15 11:53:16 BasementDesktop kernel: [ 1961.720375] sd 7:0:0:2: Power-on or device reset occurred
Jan 15 11:53:16 BasementDesktop kernel: [ 1961.726395] sd 7:0:0:0: [sdd] Attached SCSI removable disk
Jan 15 11:53:16 BasementDesktop kernel: [ 1961.738432] sd 7:0:0:1: [sde] Attached SCSI removable disk
Jan 15 11:53:16 BasementDesktop kernel: [ 1961.741558] sd 7:0:0:2: [sdf] Attached SCSI removable disk

Output from terminal command "df":

Filesystem     1K-blocks     Used Available Use% Mounted on
udev             1952856        0   1952856   0% /dev
tmpfs             403000     1824    401176   1% /run
/dev/sda6      477600624 48286480 404983600  11% /
tmpfs            2014984        0   2014984   0% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            2014984        0   2014984   0% /sys/fs/cgroup
/dev/loop0          9344     9344         0 100% /snap/canonical-livepatch/95
/dev/loop1        100224   100224         0 100% /snap/core/10577
/dev/loop3         56704    56704         0 100% /snap/core18/1932
/dev/loop2        100352   100352         0 100% /snap/core/10583
/dev/loop4         56832    56832         0 100% /snap/core18/1944
/dev/loop6        223232   223232         0 100% /snap/gnome-3-34-1804/60
/dev/loop5         82048    82048         0 100% /snap/ffmpeg/1286
/dev/loop7        224256   224256         0 100% /snap/gnome-3-34-1804/66
/dev/loop8         65920    65920         0 100% /snap/gtk-common-themes/1513
/dev/loop9         66432    66432         0 100% /snap/gtk-common-themes/1514
/dev/loop10       198016   198016         0 100% /snap/mailspring/488
/dev/loop11        52352    52352         0 100% /snap/snap-store/498
/dev/loop12        52352    52352         0 100% /snap/snap-store/518
/dev/loop13        31872    31872         0 100% /snap/snapd/10707
/dev/loop14        31872    31872         0 100% /snap/snapd/10492
/dev/loop15       297472   297472         0 100% /snap/vlc/1700
/dev/sda5         523248        4    523244   1% /boot/efi
tmpfs             402996       40    402956   1% /run/user/1000

I see 3 usb symbol "drives" in Disks, labled: "Drive Kobo Inc. Kobo Vox" where the "Volume" displays "No media"

I suspect there is a means of mounting this, but need some direction.
I tried editing mount options in Disks, with no success, but I don't know what setting to apply.
Thanks in advance for any help offered.

---

### Post by CelticWarrior on 2021-01-16
Apparently those eReaders either work autonomously via WiFi or with a computer via proprietary software that ISN'T available for Linux/Ubuntu.
Please check your manual / contact the vendor for additional info.

---

