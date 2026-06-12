---
title: "NUC5i7RYH crashing in ubuntu 14.04"
date: 2015-12-07
forum: General Help
---

### Post by replab_robin on 2015-12-07
My boss asked me to set him up with an NUC (current computer locks up with two screens).
 
I have gone for
 
NUC5I7RYH  cpu model name : Intel(R) Core(TM) i7-5557U CPU @ 3.10GHz
Kingston HyperX Predator—240 GB SHPM2280P2/240G
Kingston KVR16LS11/4 4 GB 1600 MHz x 2 ie 8GB memory
 
I have installed Ubuntu 14.04.3 LTS and fully upgraded it. The NUC Bios appears to be the very latest.
 
System is mainly working well, but I have encountered a repeatable crash running Virtualbox when trying to import a
Microsoft Windows 10 + MSEdge test appliance(.ova). The crash seems to cause complete loss of access to the file
system (the underlying drive appears OK, but the system seems to be running in memory only). I try doing ls and see 
messages in the shell /bin/ls not found etc etc. 

I originally had this crash with Virtualbox 5.03, but have downgraded to whatever 14.04.3 considers the latest and
still see the crash.
 
I have looked in the logs, but cannot see anything related to the crash which I suppose is reasonable given that we lose
access to the disk.
 
I have exploded a different MS .ova (for IE9+ Windows 7) on the NUC and I have exploded the offending .ova on another
linux box with the same software.
 
Any ideas where I should start trying to figure this out?

Only messages I see in the kern boot log look like this

Dec  7 15:57:31 machine kernel: [    0.148774] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
........
Dec  7 15:57:31 machine kernel: [    1.372753] [drm:gen8_irq_handler [i915_bpo]] *ERROR* The master control interrupt lied (SDE)!
repeated many times

Any advice much appreciated.

---

### Post by replab_robin on 2015-12-10
After configuring ryslog to send all to a nearby box I see this in the crash log; seems like some kind of disk IO error is the problem

Dec  9 17:09:56 machine kernel: [  827.367114] capability: warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Dec  9 17:09:56 machine kernel: [  827.367114] capability: warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Dec  9 17:11:41 machine kernel: [  932.533645] ata1.00: exception Emask 0x0 SAct 0x78000 SErr 0x0 action 0x6 frozen
Dec  9 17:11:41 machine kernel: [  932.533650] ata1.00: failed command: WRITE FPDMA QUEUED
Dec  9 17:11:41 machine kernel: [  932.533655] ata1.00: cmd 61/80:78:80:52:15/35:00:00:00:00/40 tag 15 ncq 7012352 out
Dec  9 17:11:41 machine kernel: [  932.533655]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  9 17:11:41 machine kernel: [  932.533657] ata1.00: status: { DRDY }
Dec  9 17:11:41 machine kernel: [  932.533645] ata1.00: exception Emask 0x0 SAct 0x78000 SErr 0x0 action 0x6 frozen
Dec  9 17:11:41 machine kernel: [  932.533650] ata1.00: failed command: WRITE FPDMA QUEUED
Dec  9 17:11:41 machine kernel: [  932.533655] ata1.00: cmd 61/80:78:80:52:15/35:00:00:00:00/40 tag 15 ncq 7012352 out
Dec  9 17:11:41 machine kernel: [  932.533655]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  9 17:11:41 machine kernel: [  932.533657] ata1.00: status: { DRDY }
Dec  9 17:11:41 machine kernel: [  932.533659] ata1.00: failed command: READ FPDMA QUEUED
Dec  9 17:11:41 machine kernel: [  932.533662] ata1.00: cmd 60/00:80:f0:bb:5a/01:00:00:00:00/40 tag 16 ncq 131072 in
Dec  9 17:11:41 machine kernel: [  932.533662]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  9 17:11:41 machine kernel: [  932.533663] ata1.00: status: { DRDY }
Dec  9 17:11:41 machine kernel: [  932.533665] ata1.00: failed command: READ FPDMA QUEUED
Dec  9 17:11:41 machine kernel: [  932.533667] ata1.00: cmd 60/00:88:f0:bc:5a/01:00:00:00:00/40 tag 17 ncq 131072 in
Dec  9 17:11:41 machine kernel: [  932.533667]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  9 17:11:41 machine kernel: [  932.533669] ata1.00: status: { DRDY }
Dec  9 17:11:41 machine kernel: [  932.533670] ata1.00: failed command: WRITE FPDMA QUEUED
Dec  9 17:11:41 machine kernel: [  932.533673] ata1.00: cmd 61/80:90:c0:6b:54/00:00:0d:00:00/40 tag 18 ncq 65536 out
Dec  9 17:11:41 machine kernel: [  932.533673]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  9 17:11:41 machine kernel: [  932.533675] ata1.00: status: { DRDY }
Dec  9 17:11:41 machine kernel: [  932.533678] ata1: hard resetting link
Dec  9 17:11:41 machine kernel: [  932.533659] ata1.00: failed command: READ FPDMA QUEUED
Dec  9 17:11:41 machine kernel: [  932.533662] ata1.00: cmd 60/00:80:f0:bb:5a/01:00:00:00:00/40 tag 16 ncq 131072 in
Dec  9 17:11:41 machine kernel: [  932.533662]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  9 17:11:41 machine kernel: [  932.533663] ata1.00: status: { DRDY }
Dec  9 17:11:41 machine kernel: [  932.533665] ata1.00: failed command: READ FPDMA QUEUED
Dec  9 17:11:41 machine kernel: [  932.533667] ata1.00: cmd 60/00:88:f0:bc:5a/01:00:00:00:00/40 tag 17 ncq 131072 in
Dec  9 17:11:41 machine kernel: [  932.533667]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  9 17:11:41 machine kernel: [  932.533669] ata1.00: status: { DRDY }
Dec  9 17:11:41 machine kernel: [  932.533670] ata1.00: failed command: WRITE FPDMA QUEUED
Dec  9 17:11:41 machine kernel: [  932.533673] ata1.00: cmd 61/80:90:c0:6b:54/00:00:0d:00:00/40 tag 18 ncq 65536 out
Dec  9 17:11:41 machine kernel: [  932.533673]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  9 17:11:41 machine kernel: [  932.533675] ata1.00: status: { DRDY }
Dec  9 17:11:41 machine kernel: [  932.533678] ata1: hard resetting link
Dec  9 17:11:42 machine kernel: [  933.357435] ata1: SATA link down (SStatus 130 SControl 300)
Dec  9 17:11:42 machine kernel: [  933.357435] ata1: SATA link down (SStatus 130 SControl 300)
Dec  9 17:11:47 machine kernel: [  938.356094] ata1: hard resetting link
Dec  9 17:11:47 machine kernel: [  938.356094] ata1: hard resetting link
Dec  9 17:11:48 machine kernel: [  939.179900] ata1: SATA link down (SStatus 130 SControl 300)
Dec  9 17:11:48 machine kernel: [  939.179908] ata1: limiting SATA link speed to 3.0 Gbps
Dec  9 17:11:48 machine kernel: [  939.179900] ata1: SATA link down (SStatus 130 SControl 300)
Dec  9 17:11:48 machine kernel: [  939.179908] ata1: limiting SATA link speed to 3.0 Gbps
Dec  9 17:11:53 machine kernel: [  944.178581] ata1: hard resetting link
Dec  9 17:11:53 machine kernel: [  944.178581] ata1: hard resetting link
Dec  9 17:11:54 machine kernel: [  945.002341] ata1: SATA link down (SStatus 120 SControl 320)
Dec  9 17:11:54 machine kernel: [  945.002348] ata1.00: disabled
Dec  9 17:11:54 machine kernel: [  945.002355] ata1.00: device reported invalid CHS sector 0
Dec  9 17:11:54 machine kernel: [  945.002356] ata1.00: device reported invalid CHS sector 0
Dec  9 17:11:54 machine kernel: [  945.002357] ata1.00: device reported invalid CHS sector 0
Dec  9 17:11:54 machine kernel: [  945.002359] ata1.00: device reported invalid CHS sector 0
Dec  9 17:11:54 machine kernel: [  945.002341] ata1: SATA link down (SStatus 120 SControl 320)
Dec  9 17:11:54 machine kernel: [  945.002348] ata1.00: disabled
Dec  9 17:11:54 machine kernel: [  945.002355] ata1.00: device reported invalid CHS sector 0
Dec  9 17:11:54 machine kernel: [  945.002356] ata1.00: device reported invalid CHS sector 0
Dec  9 17:11:54 machine kernel: [  945.002357] ata1.00: device reported invalid CHS sector 0
Dec  9 17:11:54 machine kernel: [  945.002359] ata1.00: device reported invalid CHS sector 0
Dec  9 17:11:54 machine kernel: [  945.506242] sd 0:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec  9 17:11:54 machine kernel: [  945.506246] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
Dec  9 17:11:54 machine kernel: [  945.506247] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
Dec  9 17:11:54 machine kernel: [  945.506248] sd 0:0:0:0: [sda] CDB: 
Dec  9 17:11:54 machine kernel: [  945.506249] Write(10): 2a 00 00 15 52 80 00 35 80 00
Dec  9 17:11:54 machine kernel: [  945.506254] blk_update_request: I/O error, dev sda, sector 1397376
Dec  9 17:11:54 machine kernel: [  945.506257] EXT4-fs warning (device sda2): ext4_end_bio:317: I/O error -5 writing to inode 6554854 (offset 25165824 size 8388608 starting block 174840)

---

### Post by geekgee on 2016-01-01
Hi replab_robin,

Did you ever find a solution to this?  I came across your post on the Intel forums then came here to see if you posted as well as someone suggested you do.

I have an almost identical configuration... hardware-wise the only differences are I went with a pair of the 8GB flavour of the same SODIMM line (KVR16LS11/8) and added a WD Blue 1TB Hard Drive.  My Ubuntu install is on the SSD though.

I was using Ubuntu Mate 15.10 and importing a PC-BSD 10.2 OVA into VirtualBox, can't recall if latest version or the one from the Ubuntu repos, and had the same exact issue.  It appeared the filesystem sort of dropped out from under it.  I had to cycle power to get it working again.

I didn't troubleshoot it to any great extent as I was only giving VirtualBox a quick try, I use VMware Workstation Pro on my main Ubuntu 14.04 workstation, but have had general instabilities on the NUC which I thought the VirtualBox issue may have only been a symptom of.

Thanks,

Howard

---

