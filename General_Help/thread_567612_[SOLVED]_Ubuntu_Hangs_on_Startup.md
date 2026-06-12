---
title: "[SOLVED] Ubuntu Hangs on Startup"
date: 2007-10-04
forum: General Help
---

### Post by tj111 on 2007-10-04
I'm not entirely new to linux, I am new to using linux as an OS though (work with linux servers at work from time to time, all SSH).  However when booting, Ubuntu hangs at about 3 notches in in the bar.  Without quiet mode enabled, here's what it shows.
> 
[   17.484330] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   17.669251] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.669273] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.778329] ata1: port is slow to respond, please be patient (Status 0xd0)
[   42.699251] ata1: port failed to respond (30 secs, Status 0xd0)
[   42.699258] ata1: soft resetting port
[   42.865197] ATA: abnormal status 0x7F on port 0x000101f7
[   43.194658] ata1.01: configured for UDMA/33
[   43.194677] ata1: EH complete
[   44.200600] ata1.01: ATAPI check failed
[   44.200638] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   44.200642] ata1.01: (BMDMA stat 0x45)
[   44.200648] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 254 in
[   44.200649]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x3 (HSM violation)
[   44.200675] ata1: soft resetting port
[   44.366655] ATA: abnormal status 0x7F on port 0x000101f7
[   44.542474] ATA: abnormal status 0xD0 on port 0x000101f7
[   44.542503] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[   44.542506] ata1.01: revalidation failed (errno=-5)
[   44.542510] ata1: failed to recover some devices, retrying in 5 secs
[   56.531716] ata1: port is slow to respond, please be patient (Status 0xd0)
[   79.508542] ata1: port failed to respond (30 secs, Status 0xd0)
[   79.508549] ata1: soft resetting port
[   79.674488] ATA: abnormal status 0x7F on port 0x000101f7
[   80.003965] ata1.01: configured for UDMA/33
[   80.003986] ata1: EH complete
[   81.001219] ata1.01: ATAPI check failed
[   81.001257] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   81.001261] ata1.01: (BMDMA stat 0x45)
[   81.001267] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 254 in
[   81.001268]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x3 (HSM violation)
[   81.001293] ata1: soft resetting port
[   81.167962] ATA: abnormal status 0x7F on port 0x000101f7
[   81.343780] ATA: abnormal status 0xD0 on port 0x000101f7
[   81.343808] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[   81.343811] ata1.01: revalidation failed (errno=-5)
[   81.343815] ata1: failed to recover some devices, retrying in 5 secs
[   93.333025] ata1: port is slow to respond, please be patient (Status 0xd0)
[  116.309848] ata1: port failed to respond (30 secs, Status 0xd0)
[  116.309855] ata1: soft resetting port
[  116.475786] ATA: abnormal status 0x7F on port 0x000101f7
[  116.805272] ata1.01: configured for UDMA/33
[  116.805290] ata1: EH complete


I think this may be referring to my cdr/rw drive, as it's the only PATA device I can think of (dvdr/rw and hdd are SATA).

When I just go to my computer folder (computer:///) it shows both drives, however even if there is a disc in the drive I get the error "Unable to Mount Media.  There is Probably no Media in the Drive".  I did a dmesg | tail -n 100 (to display all ata errors, shortened for brevity) and this is the contents (look familiar?)

> 
[41058.983484] ata1.01: ATAPI check failed
[41058.983525] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[41058.983533] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[41058.983534]          res 51/21:03:00:00:20/00:00:00:00:00/b0 Emask 0x3 (HSM violation)
[41058.983559] ata1: soft resetting port
[41059.150567] ATA: abnormal status 0x7F on port 0x000101f7
[41059.326429] ATA: abnormal status 0xD0 on port 0x000101f7
[41059.326464] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[41059.326468] ata1.01: revalidation failed (errno=-5)
[41059.326472] ata1: failed to recover some devices, retrying in 5 secs
[41071.315558] ata1: port is slow to respond, please be patient (Status 0xd0)
[41094.308357] ata1: port failed to respond (30 secs, Status 0xd0)
[41094.308365] ata1: soft resetting port
[41094.474394] ATA: abnormal status 0x7F on port 0x000101f7
[41094.803779] ata1.01: configured for UDMA/33
[41094.803797] ata1: EH complete
[41095.795546] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[41095.795554] ata1.01: (BMDMA stat 0x44)
[41095.795563] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[41095.795565]          res 18/01:01:01:14:eb/00:00:00:00:00/b0 Emask 0x2 (HSM violation)
[41095.795590] ata1: soft resetting port
[41095.963882] ATA: abnormal status 0x7F on port 0x000101f7
[41096.139663] ATA: abnormal status 0xD0 on port 0x000101f7
[41096.139696] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[41096.139700] ata1.01: revalidation failed (errno=-5)
.....etc


I'm a little confused where this problem is, or how to go about fixing.  Thanks for any help.

---

### Post by tj111 on 2007-10-04
Oh, I'm using FF 7.04.

---

### Post by tj111 on 2007-10-04
Followed the advice [here](https://bugs.launchpad.net/ubuntu/+bug/104581/comments/25).

---

