---
title: "ERROR: '._.com.apple.timemachine.donotpresent' has invalid checksum"
date: 2016-11-22
forum: General Help
---

### Post by baisuzhen22 on 2016-11-22
I am trying to mount a WD external hard drive. It was able to mount before, however now I receive the below message. The external has two partitions, the first one is the one that will not mount. However the second partition does. They both are exfat. I use linux distro ubuntu, not mac, so I am confused as to why I am receiving this message. 

Error mounting system-managed device /dev/sdb1: Command-line `mount "/mnt/usb-WD_Elements_1042_575831314543314A4E343033-0:0-part1"' exited with non-zero exit status 1:
stdout: `FUSE exfat 1.2.3
'
stderr: `ERROR: '._.com.apple.timemachine.donotpresent' has invalid checksum (0xc1e4 != 0xbbf4).
'
Any help would be much appreciated!

---

### Post by QIII on 2016-11-22
Is this installed on Apple hardware?

---

### Post by baisuzhen22 on 2016-11-22
Thank you for the reply. The computer I am using is a Lenovo Thinkpad T400. That's why the message is perplexing.

---

### Post by QIII on 2016-11-22
Was the drive ever connected to an Apple computer?  Was the drive used as the target for Time Machine backups?

---

### Post by baisuzhen22 on 2016-11-22
Years ago I believe I copied a few files from an imac computer.

---

### Post by QIII on 2016-11-22
OK.  That was just a thought.

I'm wondering about exfat re: corruption or an update/kernel update.  When was the last time you updated/upgraded and when did this start in relation to that?

---

### Post by baisuzhen22 on 2016-11-23
Thank you for answering my question. I plugged my external into my friend's Macbook and was able to use Disk Repair and it works fine now. I'm just still confused as to why it would have this issue years after using a mac. I also had recently reformatting the external.

---

