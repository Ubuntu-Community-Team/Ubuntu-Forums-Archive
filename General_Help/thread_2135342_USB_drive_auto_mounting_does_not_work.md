---
title: "USB drive auto mounting does not work"
date: 2013-04-14
forum: General Help
---

### Post by lavi17 on 2013-04-14
Recently i installed Ubuntu 12.10 on vmware, later installed vmware-tools on the virtual os, before that everything was working fine in terms when i plugged usb drive to the laptop, it detected and showed it, as in nomal case with usb drive name as in htp_220w. After the installation on vmware-tools on virtual os, i tried mounting my usb drive on vitual os, it gave me a message "In order to mount the drive on virtual os, it has to be unmounted from the host os, first, do you want to proceed", sort of, and i proceeded with that. Well the usb drive never got detected on virtual os, neither on the host one, i mean i can manually mount on the host OS, that works, but auto mounting does not work any longer. I went through several forum posting, the closest match so far has been, [http://ubuntuforums.org/showthread.php?t=1964198]("http://ubuntuforums.org/showthread.php?t=1964198"), i'm getting the same error under /var/log/syslog

```
Apr 14 10:01:42 lavi-Lenovo-G560 kernel: [ 2158.465748] usb 2-1.1: new high-speed USB device number 6 using ehci_hcd
Apr 14 10:01:42 lavi-Lenovo-G560 mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Apr 14 10:01:42 lavi-Lenovo-G560 kernel: [ 2158.561733] scsi5 : usb-storage 2-1.1:1.0
Apr 14 10:01:42 lavi-Lenovo-G560 mtp-probe: bus: 2, device: 6 was not an MTP device
Apr 14 10:01:43 lavi-Lenovo-G560 kernel: [ 2160.220693] scsi 5:0:0:0: Direct-Access     hp       v220w            1.00 PQ: 0 ANSI: 4
Apr 14 10:01:43 lavi-Lenovo-G560 kernel: [ 2160.223223] sd 5:0:0:0: Attached scsi generic sg2 type 0
Apr 14 10:01:43 lavi-Lenovo-G560 kernel: [ 2160.227591] sd 5:0:0:0: [sdb] 62816256 512-byte logical blocks: (32.1 GB/29.9 GiB)
Apr 14 10:01:43 lavi-Lenovo-G560 kernel: [ 2160.229457] sd 5:0:0:0: [sdb] Write Protect is off
Apr 14 10:01:43 lavi-Lenovo-G560 kernel: [ 2160.229465] sd 5:0:0:0: [sdb] Mode Sense: 2f 00 00 00
Apr 14 10:01:43 lavi-Lenovo-G560 kernel: [ 2160.231233] sd 5:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 14 10:01:43 lavi-Lenovo-G560 kernel: [ 2160.239859]  sdb: sdb1
Apr 14 10:01:43 lavi-Lenovo-G560 kernel: [ 2160.247051] sd 5:0:0:0: [sdb] Attached SCSI removable disk
```


but there is no solution provided.. If anyone has come across this issue and can help me in resolving that... Thanks in advance.

---

### Post by lavi17 on 2013-04-14
Well on one of the forums it was mentioned to check the disk-utility, so ran that, i can see the usb drive there.. i click on mount and it is visible now, i mean the usb drive is mounted now, but i guess this is what i have to do everytime for every usb disk that is to go to disk-utlity and mount it from there for now.

Though it works fine for me, just curious, how this thing works, and if it really has something to do with that mtp error, and how this can be fixed.

---

