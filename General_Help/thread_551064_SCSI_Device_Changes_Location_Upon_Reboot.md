---
title: "SCSI Device Changes Location Upon Reboot"
date: 2007-09-14
forum: General Help
---

### Post by wwiley on 2007-09-14
I have a dell PowerEdge 1650 with an attached SCSI Raid Array.  Right now it is mounted as:

/dev/sda        /data   ext3    defaults        0       0

in /etc/fstab.  I noticed when I reboot, the /data mount is not mounted.  Every time I reboot, the device location changes from /dev/sda to /dev/sdc/ and vice versa.  Any ideas why it would do this?

BTW Ubuntu 7.04 2.6.20-15-server

Any help would be appreciated.

Thanks.

---

### Post by rbmorse on 2007-09-14
I don't know why this happens, but I see the same behavior. 

Do RAID arrays get UUIDs?

---

### Post by wwiley on 2007-09-24
Im not sure what a UUID is.... all I know is that I the RAID is being done at the hardware level and presented to the OS as just a disk device.  Essentially Ubuntu sees it as just a big hard drive.  Its quite puzzling though why it changes when you reboot.

---

