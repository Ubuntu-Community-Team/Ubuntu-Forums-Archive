---
title: "External USB drives not mounting"
date: 2015-03-08
forum: General Help
---

### Post by Kymus on 2015-03-08
After a reboot. They were working fine prior to that.

This has happened before, and generally I just click the icon in the launcher, and it mounts and everything is fine. Nope, not this time.

I tried unplugging both drives, plugged them in to my other PC (Ubuntu 14.10), and I had no trouble mounting and accessing the files. I unmounted, plugged them back in to the original machine (running Ubuntu 13.10) and still nothing.

Suggestions?

---

### Post by Kymus on 2015-03-10
bumping

---

### Post by yancek on 2015-03-10
If you have one of these flash drives plugged in on boot, is it detected in the BIOS?
Have you tried manually mounting them?

---

### Post by Kymus on 2015-03-10
Hi Yancek,

I doubt it matters at all, but they're not flash drives, they are (large) external drives connected via USB.

I'll have to check the BIOS. That is a good point. As for manual mounting, I do not know how to do this :\

---

### Post by Kymus on 2015-03-10
addendum to my original post, though it may be obvious:

Usually I will see the icon for these drives in the launcher (and then I just click to mount). Presently, the icon is not showing.

I just mention this since the way I worded it originally, it could be taken that I am saying that I'm clicking to mount but nothing is happening, when the problem is that I can't mount them (at least through the GUI) since I don't see said icon.

FWIW

---

### Post by tripp98 on 2015-03-10
make sure they are unplugged.  open a terminal window.  do sudo tail -f /var/log/syslog

this will show you what is going on when you plug it in.

plug in drive.  please post what you see in the syslog this should get you closer to finding a solution.

---

### Post by Kymus on 2015-03-10
Here's the terminal copy and paste:

```
kymus@HT:~$ sudo tail -f /var/log/syslog
[sudo] password for kymus: 
Mar 10 21:33:53 HT whoopsie[999]: online
Mar 10 21:33:54 HT whoopsie[999]: online
Mar 10 21:37:17 HT whoopsie[999]: online
Mar 10 21:38:42  whoopsie[999]: last message repeated 2 times
Mar 10 21:39:14 HT whoopsie[999]: online
Mar 10 21:40:54 HT whoopsie[999]: online
Mar 10 21:40:55 HT whoopsie[999]: online
Mar 10 21:43:05 HT whoopsie[999]: online
Mar 10 21:44:12  whoopsie[999]: last message repeated 2 times
Mar 10 21:45:46 HT NetworkManager[987]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Mar 10 21:46:21 HT whoopsie[999]: online
Mar 10 21:46:27 HT kernel: [171234.413184] usb 3-2: new high-speed USB device number 13 using ehci-pci
Mar 10 21:46:27 HT kernel: [171234.546644] usb 3-2: New USB device found, idVendor=0bc2, idProduct=ab31
Mar 10 21:46:27 HT kernel: [171234.546658] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar 10 21:46:27 HT kernel: [171234.546665] usb 3-2: Product: Backup+  Desk
Mar 10 21:46:27 HT kernel: [171234.546670] usb 3-2: Manufacturer: Seagate 
Mar 10 21:46:27 HT kernel: [171234.546675] usb 3-2: SerialNumber: NA7EEFJY
Mar 10 21:46:27 HT kernel: [171234.547036] usb-storage 3-2:1.0: USB Mass Storage device detected
Mar 10 21:46:27 HT kernel: [171234.547143] scsi17 : usb-storage 3-2:1.0
Mar 10 21:46:27 HT mtp-probe: checking bus 3, device 13: "/sys/devices/pci0000:00/0000:00:16.2/usb3/3-2"
Mar 10 21:46:27 HT mtp-probe: bus: 3, device: 13 was not an MTP device
Mar 10 21:46:28 HT kernel: [171235.546740] scsi 17:0:0:0: Direct-Access     Seagate  Backup+  Desk    0342 PQ: 0 ANSI: 6
Mar 10 21:46:28 HT kernel: [171235.547444] sd 17:0:0:0: Attached scsi generic sg1 type 0
Mar 10 21:46:28 HT kernel: [171235.553837] sd 17:0:0:0: [sdb] Spinning up disk...
Mar 10 21:46:40 HT kernel: [171241.008620] .......ready
Mar 10 21:46:40 HT kernel: [171247.090937] sd 17:0:0:0: [sdb] 1220942645 4096-byte logical blocks: (5.00 TB/4.54 TiB)
Mar 10 21:46:40 HT kernel: [171247.091858] sd 17:0:0:0: [sdb] Write Protect is off
Mar 10 21:46:40 HT kernel: [171247.091866] sd 17:0:0:0: [sdb] Mode Sense: 2b 00 10 08
Mar 10 21:46:40 HT kernel: [171247.092783] sd 17:0:0:0: [sdb] Write cache: enabled, read cache: enabled, supports DPO and FUA
Mar 10 21:46:40 HT kernel: [171247.100581] sd 17:0:0:0: [sdb] 1220942645 4096-byte logical blocks: (5.00 TB/4.54 TiB)
Mar 10 21:46:40 HT kernel: [171247.126822]  sdb: sdb1
Mar 10 21:46:40 HT kernel: [171247.129791] sd 17:0:0:0: [sdb] 1220942645 4096-byte logical blocks: (5.00 TB/4.54 TiB)
Mar 10 21:46:40 HT kernel: [171247.131284] sd 17:0:0:0: [sdb] Attached SCSI disk
Mar 10 21:46:55 HT kernel: [171262.643876] usb 3-1: new high-speed USB device number 14 using ehci-pci
Mar 10 21:46:55 HT kernel: [171262.780943] usb 3-1: New USB device found, idVendor=1058, idProduct=1021
Mar 10 21:46:55 HT kernel: [171262.780959] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar 10 21:46:55 HT kernel: [171262.780966] usb 3-1: Product: Ext HDD 1021
Mar 10 21:46:55 HT kernel: [171262.780972] usb 3-1: Manufacturer: Western Digital
Mar 10 21:46:55 HT kernel: [171262.780977] usb 3-1: SerialNumber: 574341575A30353032373839
Mar 10 21:46:55 HT kernel: [171262.782302] usb-storage 3-1:1.0: USB Mass Storage device detected
Mar 10 21:46:55 HT kernel: [171262.785904] scsi18 : usb-storage 3-1:1.0
Mar 10 21:46:55 HT mtp-probe: checking bus 3, device 14: "/sys/devices/pci0000:00/0000:00:16.2/usb3/3-1"
Mar 10 21:46:55 HT mtp-probe: bus: 3, device: 14 was not an MTP device
Mar 10 21:46:56 HT kernel: [171263.786853] scsi 18:0:0:0: Direct-Access     WD       Ext HDD 1021     2021 PQ: 0 ANSI: 4
Mar 10 21:46:56 HT kernel: [171263.787101] sd 18:0:0:0: Attached scsi generic sg2 type 0
Mar 10 21:46:56 HT kernel: [171263.787878] sd 18:0:0:0: [sdc] 732566016 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Mar 10 21:46:56 HT kernel: [171263.791522] sd 18:0:0:0: [sdc] Write Protect is off
Mar 10 21:46:56 HT kernel: [171263.791536] sd 18:0:0:0: [sdc] Mode Sense: 17 00 10 08
Mar 10 21:46:56 HT kernel: [171263.793608] sd 18:0:0:0: [sdc] No Caching mode page found
Mar 10 21:46:56 HT kernel: [171263.793620] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Mar 10 21:46:56 HT kernel: [171263.796517] sd 18:0:0:0: [sdc] 732566016 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Mar 10 21:46:56 HT kernel: [171263.800627] sd 18:0:0:0: [sdc] No Caching mode page found
Mar 10 21:46:56 HT kernel: [171263.800637] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Mar 10 21:46:56 HT kernel: [171263.821819]  sdc: sdc1
Mar 10 21:46:56 HT kernel: [171263.823616] sd 18:0:0:0: [sdc] 732566016 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Mar 10 21:46:56 HT kernel: [171263.827604] sd 18:0:0:0: [sdc] No Caching mode page found
Mar 10 21:46:56 HT kernel: [171263.827611] sd 18:0:0:0: [sdc] Assuming drive cache: write through
Mar 10 21:46:56 HT kernel: [171263.827617] sd 18:0:0:0: [sdc] Attached SCSI disk

```

---

### Post by Kymus on 2015-03-14
I decided to try something different and unplug the drives, reboot, and *then* plug them in. Things are fine now. Marking thread as solved.

---

