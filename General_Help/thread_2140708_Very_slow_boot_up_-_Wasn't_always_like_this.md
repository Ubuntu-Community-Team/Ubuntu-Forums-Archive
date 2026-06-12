---
title: "Very slow boot up - Wasn't always like this"
date: 2013-04-30
forum: General Help
---

### Post by niceguy123 on 2013-04-30
I am running 12.04 32 bit (on a 64 bit laptop). Have been using this setup for over a year with no issues. Over the past couple of days the computer takes a very very long time to boot up. I have no idea why this is happening. (I am sorry to say that this is reminding me of ms windows which I haven't used in a very long time). 

I have backed up all of my files on a cloud and am emotionally ready to (format the hard drive and) re-install a fresh installation of Ubuntu. Do I need to do that?

I haven't used the Disk drive in a very long time and think that it might not be reliable for a hardboot. If so, is there a way to do this with a USB drive? What size USB drive would I need and how is that done?

Thanks for any advice.

---

### Post by zero2xiii on 2013-04-30
Hay,
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Have a view at dmesg right after boot to see if there might be any issues, post output of the following here, maybe someone spots something that might cause it.

```
dmesg | tail -n100
```

The last 100 lines should be enough to spot an issue.

Cheers

---

### Post by niceguy123 on 2013-04-30
> **zero2xiii said:**
> Hay,
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Have a view at dmesg right after boot to see if there might be any issues, post output of the following here, maybe someone spots something that might cause it.

```
dmesg | tail -n100
```

The last 100 lines should be enough to spot an issue.

Cheers

Thanks 

```
[  436.650196] ata1: EH complete
[  440.693331] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  440.693335] ata1.00: irq_stat 0x40000008
[  440.693338] ata1.00: failed command: READ FPDMA QUEUED
[  440.693343] ata1.00: cmd 60/08:00:68:cb:66/00:00:1f:00:00/40 tag 0 ncq 4096 in
[  440.693345]          res 41/40:08:68:cb:66/00:00:1f:00:00/6f Emask 0x409 (media error) <F>
[  440.693347] ata1.00: status: { DRDY ERR }
[  440.693350] ata1.00: error: { UNC }
[  440.695158] ata1.00: configured for UDMA/100
[  440.695166] sd 0:0:0:0: [sda] Unhandled sense code
[  440.695168] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  440.695172] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  440.695177] Descriptor sense data with sense descriptors (in hex):
[  440.695179]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  440.695189]         1f 66 cb 68 
[  440.695193] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  440.695199] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 1f 66 cb 68 00 00 08 00
[  440.695209] end_request: I/O error, dev sda, sector 526830440
[  440.695222] ata1: EH complete
[  444.793863] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  444.793867] ata1.00: irq_stat 0x40000008
[  444.793870] ata1.00: failed command: READ FPDMA QUEUED
[  444.793876] ata1.00: cmd 60/08:00:68:cb:66/00:00:1f:00:00/40 tag 0 ncq 4096 in
[  444.793877]          res 41/40:08:68:cb:66/00:00:1f:00:00/6f Emask 0x409 (media error) <F>
[  444.793880] ata1.00: status: { DRDY ERR }
[  444.793882] ata1.00: error: { UNC }
[  444.795687] ata1.00: configured for UDMA/100
[  444.795695] ata1: EH complete
[  448.716631] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  448.716635] ata1.00: irq_stat 0x40000008
[  448.716638] ata1.00: failed command: READ FPDMA QUEUED
[  448.716644] ata1.00: cmd 60/08:00:68:cb:66/00:00:1f:00:00/40 tag 0 ncq 4096 in
[  448.716645]          res 41/40:08:68:cb:66/00:00:1f:00:00/6f Emask 0x409 (media error) <F>
[  448.716648] ata1.00: status: { DRDY ERR }
[  448.716650] ata1.00: error: { UNC }
[  448.718478] ata1.00: configured for UDMA/100
[  448.718485] ata1: EH complete
[  452.639300] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  452.639303] ata1.00: irq_stat 0x40000008
[  452.639306] ata1.00: failed command: READ FPDMA QUEUED
[  452.639312] ata1.00: cmd 60/08:00:68:cb:66/00:00:1f:00:00/40 tag 0 ncq 4096 in
[  452.639313]          res 41/40:08:68:cb:66/00:00:1f:00:00/6f Emask 0x409 (media error) <F>
[  452.639316] ata1.00: status: { DRDY ERR }
[  452.639318] ata1.00: error: { UNC }
[  452.641120] ata1.00: configured for UDMA/100
[  452.641126] ata1: EH complete
[  456.562027] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  456.562030] ata1.00: irq_stat 0x40000008
[  456.562033] ata1.00: failed command: READ FPDMA QUEUED
[  456.562039] ata1.00: cmd 60/08:00:68:cb:66/00:00:1f:00:00/40 tag 0 ncq 4096 in
[  456.562040]          res 41/40:08:68:cb:66/00:00:1f:00:00/6f Emask 0x409 (media error) <F>
[  456.562043] ata1.00: status: { DRDY ERR }
[  456.562045] ata1.00: error: { UNC }
[  456.563846] ata1.00: configured for UDMA/100
[  456.563856] ata1: EH complete
[  460.506973] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  460.506977] ata1.00: irq_stat 0x40000008
[  460.506980] ata1.00: failed command: READ FPDMA QUEUED
[  460.506986] ata1.00: cmd 60/08:00:68:cb:66/00:00:1f:00:00/40 tag 0 ncq 4096 in
[  460.506987]          res 41/40:08:68:cb:66/00:00:1f:00:00/6f Emask 0x409 (media error) <F>
[  460.506990] ata1.00: status: { DRDY ERR }
[  460.506992] ata1.00: error: { UNC }
[  460.508794] ata1.00: configured for UDMA/100
[  460.508800] ata1: EH complete
[  464.540828] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  464.540832] ata1.00: irq_stat 0x40000008
[  464.540835] ata1.00: failed command: READ FPDMA QUEUED
[  464.540840] ata1.00: cmd 60/08:00:68:cb:66/00:00:1f:00:00/40 tag 0 ncq 4096 in
[  464.540841]          res 41/40:08:68:cb:66/00:00:1f:00:00/6f Emask 0x409 (media error) <F>
[  464.540844] ata1.00: status: { DRDY ERR }
[  464.540847] ata1.00: error: { UNC }
[  464.542656] ata1.00: configured for UDMA/100
[  464.542663] sd 0:0:0:0: [sda] Unhandled sense code
[  464.542665] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  464.542669] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  464.542674] Descriptor sense data with sense descriptors (in hex):
[  464.542676]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  464.542686]         1f 66 cb 68 
[  464.542690] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  464.542696] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 1f 66 cb 68 00 00 08 00
[  464.542706] end_request: I/O error, dev sda, sector 526830440
[  464.542719] ata1: EH complete
[  538.744044] usb 2-2: new high-speed USB device number 4 using ehci_hcd
[  538.918546] Initializing USB Mass Storage driver...
[  538.918732] scsi4 : usb-storage 2-2:1.0
[  538.918816] usbcore: registered new interface driver usb-storage
[  538.918818] USB Mass Storage support registered.
[  539.924362] scsi 4:0:0:0: Direct-Access     Generic  Flash Disk       8.07 PQ: 0 ANSI: 2
[  539.929853] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  539.930183] sd 4:0:0:0: [sdb] 7831552 512-byte logical blocks: (4.00 GB/3.73 GiB)
[  539.930682] sd 4:0:0:0: [sdb] Write Protect is off
[  539.930685] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  539.931184] sd 4:0:0:0: [sdb] No Caching mode page present
[  539.931187] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  539.934186] sd 4:0:0:0: [sdb] No Caching mode page present
[  539.934191] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  539.942135]  sdb: sdb1
[  539.945064] sd 4:0:0:0: [sdb] No Caching mode page present
[  539.945068] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  539.945071] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by Cheesehead on 2013-04-30
400-500 seconds after boot is too late.
We need to see dmesg during the boot (0-120 seconds), especially the delay.
Please reboot and try again, else attach (not cut-and-paste) the entire dmesg file.

---

### Post by zero2xiii on 2013-05-01
+1 for the above,

Also may I suggest running a SMART test on all your disk drives?

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sd**X**

```

replace X with all teh drive letters eg: a, b, c. To check all drives, not sda1, sda2 etc.


You can try and post the following rather:
```
dmesg --level=err,warn
```

You can try and clear the dmesg log and attach a full copy after a reboot:
please do the clearing only if the output is truncated when you run "dmesg" in terminal.

```
sudo dmesg --clear
sudo reboot now
dmesg

```

Cheers

---

