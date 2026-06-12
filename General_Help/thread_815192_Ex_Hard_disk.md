---
title: "Ex Hard disk"
date: 2008-06-01
forum: General Help
---

### Post by Zophixan on 2008-06-01
Heya, for some reason, my external hard disks are only recognised when plugged in before ubuntu boots up - I can't plug it in, and then let it recognise it, as nothing happens! Any idea why guys? Also on one of my hd's , it has stopped being seen in windows, however can still be seen in linux, any idea why that may have happened? They are all formatted as NTFS.

---

### Post by hal8000 on 2008-06-01
> **Zophixan said:**
> Heya, for some reason, my external hard disks are only recognised when plugged in before ubuntu boots up - I can't plug it in, and then let it recognise it, as nothing happens! Any idea why guys? Also on one of my hd's , it has stopped being seen in windows, however can still be seen in linux, any idea why that may have happened? They are all formatted as NTFS.

External hard drives or pen drives should cause a hotplug event to be generated. Either hal is not functioning or perhaps you have added new software or altered something?

Boot ubuntu, then plug in your external hard drive, open a terminal and
type 
dmesg

You should have something similar to the output below.

[ 5317.198074] Initializing USB Mass Storage driver...
[ 5317.200031] scsi4 : SCSI emulation for USB Mass Storage devices
[ 5317.201755] usbcore: registered new interface driver usb-storage
[ 5317.201768] USB Mass Storage support registered.
[ 5317.201924] usb-storage: device found at 3
[ 5317.201927] usb-storage: waiting for device to settle before scanning
[ 5322.189660] usb-storage: device scan complete
[ 5322.190781] scsi 4:0:0:0: Direct-Access     Easy     Disk             V1.1 PQ: 0 ANSI: 0 CCS
[ 5322.863877] sd 4:0:0:0: [sdc] 2015232 512-byte hardware sectors (1032 MB)
[ 5322.864504] sd 4:0:0:0: [sdc] Write Protect is off
[ 5322.864512] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 5322.864516] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 5322.867115] sd 4:0:0:0: [sdc] 2015232 512-byte hardware sectors (1032 MB)
[ 5322.868364] sd 4:0:0:0: [sdc] Write Protect is off
[ 5322.868370] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 5322.868375] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 5322.868383]  sdc: sdc1
[ 5322.869357] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[ 5322.869424] sd 4:0:0:0: Attached scsi generic sg3 type 0


Post back your results and also the output of 
lsub

when your usb hard drive is connected.

---

### Post by Zophixan on 2008-06-03
Hmm problem isn't happening anymore, strange :-s. Thanks anyway!

---

### Post by Zophixan on 2008-06-03
Whoops its come back:
Heres what i get after typing dmsg

edit: it won't let me post the code itself :S complains about having too many images? Can I email it to one of you guys? Since i can't attach it here due to it being over file size limit.

---

### Post by danwood76 on 2008-06-03
dmesg shouldnt contain images???

run this from the terminal and it should just be text output:
```

dmesg

```

---

