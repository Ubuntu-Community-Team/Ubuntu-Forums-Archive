---
title: "Interrupted fsck, now Ubuntu cannot detect hard drive at all"
date: 2023-11-29
forum: General Help
---

### Post by CRAZY_PALADIN on 2023-11-29
I have a Seagate external hard drive that has developed some bad blocks. I pulled out most of the data not affected and tried to fix the bad blocks. After reading on some online posts & tutorials, I tried to do a fsck. It went on for a long while and I had to shutdown my PC, so I interrupted the process, not knowing the consequences. (Although before the shutdown after fsck interrupted , I did see the hard drive can still be mounted and all the content still there)

After I went back, my PC can no longer detect the hard drive at all. I cannot see it with `ls /dev/ | grep sd` or `sudo fdisk -l` or `sudo lsblk -f`. The only way it does show up is through `sudo tail -f /var/log/syslog` after I plugged in the device. Is there still any hope I can salvage this situation? 

Here's the syslog btw:
```

Nov 30 10:20:30 DekstopPC kernel: [ 3088.698537] usb 2-4: new SuperSpeed USB device number 7 using xhci_hcd
Nov 30 10:20:30 DekstopPC kernel: [ 3088.723813] usb 2-4: New USB device found, idVendor=0bc2, idProduct=2037, bcdDevice=19.01
Nov 30 10:20:30 DekstopPC kernel: [ 3088.723826] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 30 10:20:30 DekstopPC kernel: [ 3088.723831] usb 2-4: Product: Expansion HDD
Nov 30 10:20:30 DekstopPC kernel: [ 3088.723835] usb 2-4: Manufacturer: Seagate
Nov 30 10:20:30 DekstopPC kernel: [ 3088.723839] usb 2-4: SerialNumber: ......
Nov 30 10:20:30 DekstopPC kernel: [ 3088.731874] scsi host6: uas
Nov 30 10:20:30 DekstopPC kernel: [ 3088.732556] scsi 6:0:0:0: Direct-Access     Seagate  Expansion HDD    1901 PQ: 0 ANSI: 6
Nov 30 10:20:30 DekstopPC mtp-probe: checking bus 2, device 7: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-4"
Nov 30 10:20:30 DekstopPC mtp-probe: bus: 2, device: 7 was not an MTP device
Nov 30 10:20:30 DekstopPC kernel: [ 3088.735047] sd 6:0:0:0: Attached scsi generic sg2 type 0
Nov 30 10:20:30 DekstopPC mtp-probe: checking bus 2, device 7: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-4"
Nov 30 10:20:30 DekstopPC mtp-probe: bus: 2, device: 7 was not an MTP device
Nov 30 10:20:54 DekstopPC kernel: [ 3113.304777] sd 6:0:0:0: [sdc] Spinning up disk...
Nov 30 10:20:56 DekstopPC kernel: [ 3114.834761] .
Nov 30 10:20:56 DekstopPC kernel: [ 3115.434798] usb 2-4: USB disconnect, device number 7
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435003] sd 6:0:0:0: [sdc] tag#1 uas_zap_pending 0 uas-tag 1 inflight: CMD 
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435011] sd 6:0:0:0: [sdc] tag#1 CDB: Test Unit Ready 00 00 00 00 00 00
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435131] ready
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435159] sd 6:0:0:0: [sdc] Read Capacity(16) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435165] sd 6:0:0:0: [sdc] Sense not available.
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435178] sd 6:0:0:0: [sdc] Read Capacity(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435181] sd 6:0:0:0: [sdc] Sense not available.
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435190] sd 6:0:0:0: [sdc] 0 512-byte logical blocks: (0 B/0 B)
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435193] sd 6:0:0:0: [sdc] 0-byte physical blocks
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435201] sd 6:0:0:0: [sdc] Write Protect is off
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435205] sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435212] sd 6:0:0:0: [sdc] Asking for cache data failed
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435219] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435233] sd 6:0:0:0: [sdc] Preferred minimum I/O size 4096 bytes not a multiple of physical block size (0 bytes)
Nov 30 10:20:56 DekstopPC kernel: [ 3115.435238] sd 6:0:0:0: [sdc] Optimal transfer size 33553920 bytes not a multiple of physical block size (0 bytes)
Nov 30 10:20:56 DekstopPC kernel: [ 3115.436031] sd 6:0:0:0: [sdc] Attached SCSI disk
Nov 30 10:20:57 DekstopPC systemd-udevd[12932]: sdc: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/sdc' failed with exit code 1.

```

---

### Post by Rubi1200 on 2023-12-01
I would suggest running the boot info script (see signature) and let's hope that gives us more information.

Choose to create a summary report and post the pastebin link back here.

Actually, while you are at it, please also run the system info script.

Best to do both from a live medium such as USB.

---

### Post by MAFoElffen on 2023-12-01
Can you see it with this? 
```

sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq

```
If you can, I would re-do fsck on it again...

If sort of, where you can see the disk, but either not the filesystem or not the partitions, then...
If it is not a boot or system disk, I would run '[testdisk]("https://www.cgsecurity.org/testdisk-7.2-WIP.linux26-x86_64.tar.bz2")' on it. 

(The right tools for the job)

---

### Post by CRAZY_PALADIN on 2023-12-01
> **Rubi1200 said:**
> I would suggest running the boot info script (see signature) and let's hope that gives us more information.

Choose to create a summary report and post the pastebin link back here.

Actually, while you are at it, please also run the system info script.

Best to do both from a live medium such as USB.

Thanks, here's the pastebin for system info: 
[https://paste.ubuntu.com/p/SSCBprSBwk/](https://paste.ubuntu.com/p/SSCBprSBwk/) 

And here's for the boot info:
[https://paste.ubuntu.com/p/py9DtndTkC/](https://paste.ubuntu.com/p/py9DtndTkC/)

I don't seem to see the Seagate drive being picked up.

> **MAFoElffen said:**
> Can you see it with this? 
```

sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq

```
If you can, I would re-do fsck on it again...

If sort of, where you can see the disk, but either not the filesystem or not the partitions, then...
If it is not a boot or system disk, I would run '[testdisk]("https://www.cgsecurity.org/testdisk-7.2-WIP.linux26-x86_64.tar.bz2")' on it. 

(The right tools for the job)
Thanks, unfortunately I didn't see the Seagate disk there, and `testdisk` also didn't see it either.

BTW, is there any tool that can still wipe the disk even in this condition (well other than a blowtorch, I might still try to claim warranty on this thing)?

---

### Post by yancek on 2023-12-01
>  tried to fix the bad blocks

How did you do that?  The general method is to use fsck.  You can't repair bad blocks on hardware, they are just marked so that the system will not try to use them.

Interrupting fsck was not a good idea.  Did you try running it again as suggested?  There are a number of ways to overwrite data and you may just need to overwrite the first few sectors.  One such tool is shred which is located in /usr/bin/.

---

### Post by CRAZY_PALADIN on 2023-12-01
> **yancek said:**
> How did you do that?  The general method is to use fsck.  You can't repair bad blocks on hardware, they are just marked so that the system will not try to use them.

Interrupting fsck was not a good idea.  Did you try running it again as suggested?  There are a number of ways to overwrite data and you may just need to overwrite the first few sectors.  One such tool is shred which is located in /usr/bin/.

As you can tell, I don't really know what I'm doing, I just read a few online posts and was trying to do stuff. I did use `fsck -f`, and after 3 hours I had to go so I interrupted it and shutdown my PC. Unfortunately the whole issue is I can't run fsck again on the device, because the system couldn't even pick it up, it's not showed up as a devices under /dev.

EDIT:
Looking back, the syslog did say it tried to do something with the drive and assign it to `/dev/sdc` with the command `/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/sdc`. I'm not sure if there's a way to manually or forcefully assign the drive under /dev

---

### Post by Rubi1200 on 2023-12-01
Did you run the scripts with the external drive plugged in?

---

### Post by CRAZY_PALADIN on 2023-12-01
Yeah it was plugged in, I double checked and I can see it in syslog again

---

### Post by MAFoElffen on 2023-12-01
In the syslog's? It is already tested and known to be a bad drive already right?

I used to volunteer for a computer recycler. If we couldn;t wipe a drive, we removed the printed circuit cards, drilled thorugh them with a drill press, then disassembled them.

---

