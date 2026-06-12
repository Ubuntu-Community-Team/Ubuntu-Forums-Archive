---
title: "Ubuntu SD Card automatic mount"
date: 2012-12-21
forum: General Help
---

### Post by jiapei100 on 2012-12-21
Hi, all:

sorry for re-opening this topic, almost exactly the same thing at
[http://ubuntuforums.org/showthread.php?t=1507558]("http://ubuntuforums.org/showthread.php?t=1507558")

Environment: Ubuntu 12.04
Question: about SD card automatic mount

1) In order to always automatically mount my SD card to a specific location, say: **/mnt/sd** ; it seems the only solution is to use **UUID** in **/etc/fstab**. Otherwise, by using **/etc/mtab**, whenever some other devices are plugged onto the computer, although the SD card can be detected by Ubuntu in **/dev/sd***, it's not guaranteed that you can always get the same device name. That's to say: some times you get **/dev/sdd**; some times you get **/dev/sde**.  

By using **/etc/mtab**, manually mount SD card by inputting a command line seems to be the only way out. This is not convenient enough.

This is also why I don't think the answer from smackwacker in the above closed topic [http://ubuntuforums.org/showthread.php?t=1507558]("http://ubuntuforums.org/showthread.php?t=1507558") is excellent enough.


2) However, by mounting SD card using** /etc/fstab**, I'll get exactly the same error message **the disk drive for  is not ready yet or not present** as mentioned in the above closed topic.



I'm wondering is there a way to finish the task like:
whenever the computer reboots, automatically disconnect all the mounted devices, no matter it's mounted through **/etc/mtab**, or through **/etc/fstab** ??

Cheers
Pei

---

### Post by dino99 on 2012-12-21
as i know, and im lazy enough to use the default settings, mountall by default mount devices; no need to disturb the system with fstab/mtab entries, let the system doing its job.
if you need/want something different, then use disk-utility.

---

