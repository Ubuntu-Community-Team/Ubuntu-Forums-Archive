---
title: "Installation Problem"
date: 2008-04-22
forum: General Help
---

### Post by bludo on 2008-04-22
Hi, I'm trying to install ubuntu using wubi but I'm having a problem. 

Every time I boot into ubuntu to complete the installation it stops and I get the chkdsk message. 

I've tried a dozen of times to install/uninstall it after running chkdsk /r on that partition and every time I get that message.

I even tried to format the partition and it didn't work. I keep getting the chkdsk message.


Do I have to install it on a primary partition? Is that why it isn't working?
Any other ideas? I wanted to give ubuntu a shot, but it seems that I'm out of luck.

Thanks

---

### Post by NightwishFan on 2008-04-22
Can you install the normal way? That is preferred if anything, rather than wubi. (wubi owns though :lolflag:)

---

### Post by ago on 2008-04-22
Uninstall/reinstall
After chooseing "ubuntu" at boot select "verbose mode"

When the error appears, reboot into windows, you should have a file called: c:\ubuntu\installation-logs.zip

Please attach it here.

Also post the wubi log in your user temp folder (%temp%)

Before rebooting please check the content of: C:\ubuntu\disks and list all the files in there and their size.

---

### Post by ago on 2008-04-22
> **NightwishFan said:**
> Can you install the normal way? That is preferred if anything, rather than wubi. (wubi owns though :lolflag:)

Well at least for today I'd like people to try wubi, since today is the last day I will be able to fix bugs...

---

### Post by bludo on 2008-04-22
Thanks for the quick reply!

I'm afraid that after choosing the verbose mode, I have no installation-logs.zip in my ubuntu folder :(

Here are the other things you requested

Thanks

---

### Post by ago on 2008-04-22
Do you see C:\ubuntu\disks\root.disk (~9GB) and C:\ubuntu\disks\swap.disk?

Also try installing again, when it stops, press CTRL+ALT+F2

And run the following command

sudo sh /custom-installation/hooks/failure-command.sh

Now the logs should be in C:\ubuntu

NOTE: this assumes that the error is during the Linux side installation: i.e. you should see a progress bar on a brown background with bird

---

### Post by bludo on 2008-04-22
Yes, I have those, and the installation problem is on the linux side, with the bird on the desktop.

I've got the logs this time, with the command that you mentioned.

Thanks!

---

### Post by ago on 2008-04-22
Edit c:\ubuntu\install\custom-installation\hooks\early-command.sh
Append the following line at the end of the file:

```
sed -i '/#!/ a set -x' /root/bin/autopartition-loop
```

When you save the document make sure that all line endings use linux convention (LF). You can use scite ([http://www.scintilla.org/SciTE.html](http://www.scintilla.org/SciTE.html)) to ensure that (under Options > Line Endings + Convert Line Ending).

Delete the old logs, and reboot, then follow the procedure above and please post the new logs again.

---

### Post by ago on 2008-04-22
sed -i '/#!/ a set -x' /root/bin/autopartition-loop

with a space after "set"

---

### Post by bludo on 2008-04-22
Done that.

Anyway, if it doesn't work, maybe I'll try a full install someday..

Thanks

---

### Post by ago on 2008-04-22
Are you sure you have a file called C:\ubuntu\disks\root.disk?

From the logs it does not look like that is the case

---

### Post by bludo on 2008-04-22
Yes, but it's at J:\ubuntu\disks\root.disk where I've installed it and it has 9GB

---

### Post by ago on 2008-04-22
Ok a few tests if you do not mind

when that fails, after you press ctrl+alt+f2, if you type

ls /host

That should be the listing of your J: drive. And you should see root.disk in

ls /host/ubuntu/disks

If it's not the J: drive than we are closing in...

---

### Post by ago on 2008-04-22
Do you have some C:\ubuntu folder from a previous installation maybe?

---

### Post by khanhvlq on 2008-04-22
In the Future, I hope "Mount CD" error is repaired!

---

### Post by ago on 2008-04-22
> **khanhvlq said:**
> In the Future, I hope "Mount CD" error is repaired!

???

---

### Post by ago on 2008-04-22
Bludo, do you have a "ubuntu" directory in any other drive other than J: ?

---

### Post by bludo on 2008-04-22
No, I don't have another ubuntu directory on any other drive.

I'll try the ls and I'll report it soon.

Thanks

---

### Post by ago on 2008-04-22
Add the following c:\ubuntu\install\custom-installation\hooks\early-command.sh
Will give me more info

```

sed -i '/#!/ a set -x' /root/bin/autopartition-loop
cat /proc/partitions > /root/var/log/proc.partitions
cat /proc/mounts >  /root/var/log/proc.mounts
cp /cutsom-installation/preseed.cfg /root/var/log/ || true
cp /root/cutsom-installation/preseed.cfg /root/var/log/ || true

```


PS Thanks a lot for the help

---

### Post by bludo on 2008-04-22
OK. ls shows me the content of C:. I have ubuntu installed on J:. This could be a hint of the problem. 

I have no Ubuntu directory on C

I have to thanks for the help :)

---

### Post by ago on 2008-04-22
bludo, last thing
when you reboot press esc after choosing "Ubuntu" and select verbose mode

Also, before running the failure-command, run the following:

sudo cp /custom-installation/preseed.cfg /var/log/

---

### Post by bludo on 2008-04-22
Here it is. I hope I've done it right.

---

### Post by ago on 2008-04-22
bludo,

The issue is that you installed on partition 10 and I get partition 1. Which seems to indicate that the number gets truncated at some stage.

You should boot adding "break=bottom" to the kernel line (/ubuntu/install/grub/menu.lst). The boot will stop at command shell. Type:

grep partman-auto /preseed.cfg

I am interested in the disk and partition values.

It also looks like the disk order alternates! For instance, in the last log, the first disk (sda) is the one with several partitions (sda10). But in the previous log the same disk appears as the second one (sdb10). Did you change anything?

That is not the issue, but it is interesting anyway, and would like more info!

---

### Post by ago on 2008-04-22
> **ago said:**
> It also looks like the disk order alternates! For instance, in the last log, the first disk (sda) is the one with several partitions (sda10). But in the previous log the same disk appears as the second one (sdb10). Did you change anything?

```

Apr 22 14:31:26 ubuntu kernel: [   34.849808] pata_amd 0000:00:06.0: version 0.3.10
Apr 22 14:31:26 ubuntu kernel: [   34.849845] PCI: Setting latency timer of device 0000:00:06.0 to 64
Apr 22 14:31:26 ubuntu kernel: [   34.849901] scsi0 : pata_amd
Apr 22 14:31:26 ubuntu kernel: [   34.849937] scsi1 : pata_amd
Apr 22 14:31:26 ubuntu kernel: [   34.850424] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Apr 22 14:31:26 ubuntu kernel: [   34.850426] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Apr 22 14:31:26 ubuntu kernel: [   34.858333] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input1
Apr 22 14:31:26 ubuntu kernel: [   34.882020] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.0-4
Apr 22 14:31:26 ubuntu kernel: [   34.897124] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/input/input2
Apr 22 14:31:26 ubuntu kernel: [   34.905976] input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.0-4
Apr 22 14:31:26 ubuntu kernel: [   34.905988] usbcore: registered new interface driver usbhid
Apr 22 14:31:26 ubuntu kernel: [   34.905991] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Apr 22 14:31:26 ubuntu kernel: [   35.344838] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4160B, A306, max UDMA/66
Apr 22 14:31:26 ubuntu kernel: [   35.344659] ata2.01: ATA-7: SAMSUNG HD300LD, WK100-12, max UDMA/100
Apr 22 14:31:26 ubuntu kernel: [   35.344663] ata2.01: 586072368 sectors, multi 16: LBA48
Apr 22 14:31:26 ubuntu kernel: [   35.512203] ata2.00: configured for UDMA/66
Apr 22 14:31:26 ubuntu kernel: [   35.528271] ata2.01: configured for UDMA/100
Apr 22 14:31:26 ubuntu kernel: [   35.531964] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4160B A306 PQ: 0 ANSI: 5
Apr 22 14:31:26 ubuntu kernel: [   35.532063] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG HD300LD  WK10 PQ: 0 ANSI: 5
Apr 22 14:31:26 ubuntu kernel: [   35.532438] sata_nv 0000:00:07.0: version 3.5
Apr 22 14:31:26 ubuntu kernel: [   35.532447] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
Apr 22 14:31:26 ubuntu kernel: [   35.532451] sata_nv 0000:00:07.0: Using ADMA mode
Apr 22 14:31:26 ubuntu kernel: [   35.532481] PCI: Setting latency timer of device 0000:00:07.0 to 64
Apr 22 14:31:26 ubuntu kernel: [   35.532767] scsi2 : sata_nv
Apr 22 14:31:26 ubuntu kernel: [   35.532874] scsi3 : sata_nv
Apr 22 14:31:26 ubuntu kernel: [   35.532992] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 20
Apr 22 14:31:26 ubuntu kernel: [   35.532994] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 20
Apr 22 14:31:26 ubuntu kernel: [   36.111449] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 22 14:31:26 ubuntu kernel: [   36.115175] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508d0000d6fa1d]
Apr 22 14:31:26 ubuntu kernel: [   36.123483] ata3.00: ATA-6: ST3200822AS, 3.01, max UDMA/133
Apr 22 14:31:26 ubuntu kernel: [   36.123485] ata3.00: 390721968 sectors, multi 16: LBA48
Apr 22 14:31:26 ubuntu kernel: [   36.135349] ata3.00: configured for UDMA/133
Apr 22 14:31:26 ubuntu kernel: [   36.446934] ata4: SATA link down (SStatus 0 SControl 300)
Apr 22 14:31:26 ubuntu kernel: [   36.447014] scsi 2:0:0:0: Direct-Access     ATA      ST3200822AS      3.01 PQ: 0 ANSI: 5
Apr 22 14:31:26 ubuntu kernel: [   36.447020] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
Apr 22 14:31:26 ubuntu kernel: [   36.447077] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
Apr 22 14:31:26 ubuntu kernel: [   36.447081] sata_nv 0000:00:08.0: Using ADMA mode
Apr 22 14:31:26 ubuntu kernel: [   36.447111] PCI: Setting latency timer of device 0000:00:08.0 to 64
Apr 22 14:31:26 ubuntu kernel: [   36.447365] scsi4 : sata_nv
Apr 22 14:31:26 ubuntu kernel: [   36.447471] scsi5 : sata_nv
Apr 22 14:31:26 ubuntu kernel: [   36.447600] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 16
Apr 22 14:31:26 ubuntu kernel: [   36.447602] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 16
Apr 22 14:31:26 ubuntu kernel: [   36.758459] ata5: SATA link down (SStatus 0 SControl 300)
Apr 22 14:31:26 ubuntu kernel: [   37.069982] ata6: SATA link down (SStatus 0 SControl 300)
Apr 22 14:31:26 ubuntu kernel: [   37.077589] Driver 'sd' needs updating - please use bus_type methods
Apr 22 14:31:26 ubuntu kernel: [   37.078717] sd 1:0:1:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
Apr 22 14:31:26 ubuntu kernel: [   37.078725] sd 1:0:1:0: [sda] Write Protect is off
Apr 22 14:31:26 ubuntu kernel: [   37.078727] sd 1:0:1:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 14:31:26 ubuntu kernel: [   37.078738] sd 1:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 14:31:26 ubuntu kernel: [   37.078774] sd 1:0:1:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
Apr 22 14:31:26 ubuntu kernel: [   37.078780] sd 1:0:1:0: [sda] Write Protect is off
Apr 22 14:31:26 ubuntu kernel: [   37.078781] sd 1:0:1:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 14:31:26 ubuntu kernel: [   37.078790] sd 1:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 14:31:26 ubuntu kernel: [   37.078793]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Apr 22 14:31:26 ubuntu kernel: [   37.091162]  sda1 sda2 < sda5 >
Apr 22 14:31:26 ubuntu kernel: [   37.112631] sd 1:0:1:0: [sda] Attached SCSI disk
Apr 22 14:31:26 ubuntu kernel: [   37.112667] sd 2:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Apr 22 14:31:26 ubuntu kernel: [   37.112674] sd 2:0:0:0: [sdb] Write Protect is off
Apr 22 14:31:26 ubuntu kernel: [   37.112675] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr 22 14:31:26 ubuntu kernel: [   37.112685] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 14:31:26 ubuntu kernel: [   37.112709] sd 2:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Apr 22 14:31:26 ubuntu kernel: [   37.112715] sd 2:0:0:0: [sdb] Write Protect is off
Apr 22 14:31:26 ubuntu kernel: [   37.112717] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr 22 14:31:26 ubuntu kernel: [   37.112730] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 14:31:26 ubuntu kernel: [   37.112732]  sdb:sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 22 14:31:26 ubuntu kernel: [   37.127263] Uniform CD-ROM driver Revision: 3.20
Apr 22 14:31:26 ubuntu kernel: [   37.127289] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 22 14:31:26 ubuntu kernel: [   37.128178]  sdb1 sdb2 < sdb5 sdb6 sdb7 sdb8 sdb9 sdb10 >
Apr 22 14:31:26 ubuntu kernel: [   37.190469] sd 2:0:0:0: [sdb] Attached SCSI disk
Apr 22 14:31:26 ubuntu kernel: [   37.193823] sr 1:0:0:0: Attached scsi generic sg0 type 5
Apr 22 14:31:26 ubuntu kernel: [   37.193838] sd 1:0:1:0: Attached scsi generic sg1 type 0
Apr 22 14:31:26 ubuntu kernel: [   37.193852] sd 2:0:0:0: Attached scsi generic sg2 type 0

```

```

Apr 22 14:56:10 ubuntu kernel: [   34.714731] sata_nv 0000:00:07.0: version 3.5
Apr 22 14:56:10 ubuntu kernel: [   34.714788] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
Apr 22 14:56:10 ubuntu kernel: [   34.714909] sata_nv 0000:00:07.0: Using ADMA mode
Apr 22 14:56:10 ubuntu kernel: [   34.714983] PCI: Setting latency timer of device 0000:00:07.0 to 64
Apr 22 14:56:10 ubuntu kernel: [   34.717568] scsi0 : sata_nv
Apr 22 14:56:10 ubuntu kernel: [   34.719609] scsi1 : sata_nv
Apr 22 14:56:10 ubuntu kernel: [   34.719795] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 20
Apr 22 14:56:10 ubuntu kernel: [   34.719842] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 20
Apr 22 14:56:10 ubuntu kernel: [   35.175677] usb 1-4: new low speed USB device using ohci_hcd and address 3
Apr 22 14:56:10 ubuntu kernel: [   35.295498] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 22 14:56:10 ubuntu kernel: [   35.303854] ata1.00: ATA-6: ST3200822AS, 3.01, max UDMA/133
Apr 22 14:56:10 ubuntu kernel: [   35.303901] ata1.00: 390721968 sectors, multi 16: LBA48
Apr 22 14:56:10 ubuntu kernel: [   35.319952] ata1.00: configured for UDMA/133
Apr 22 14:56:10 ubuntu kernel: [   35.404508] usb 1-4: configuration #1 chosen from 1 choice
Apr 22 14:56:10 ubuntu kernel: [   35.425509] usbcore: registered new interface driver hiddev
Apr 22 14:56:10 ubuntu kernel: [   35.435544] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.0/input/input1
Apr 22 14:56:10 ubuntu kernel: [   35.452277] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.0-4
Apr 22 14:56:10 ubuntu kernel: [   35.468452] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.1/input/input2
Apr 22 14:56:10 ubuntu kernel: [   35.480223] input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:02.0-4
Apr 22 14:56:10 ubuntu kernel: [   35.480418] usbcore: registered new interface driver usbhid
Apr 22 14:56:10 ubuntu kernel: [   35.480465] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Apr 22 14:56:10 ubuntu kernel: [   35.630990] ata2: SATA link down (SStatus 0 SControl 300)
Apr 22 14:56:10 ubuntu kernel: [   35.631121] scsi 0:0:0:0: Direct-Access     ATA      ST3200822AS      3.01 PQ: 0 ANSI: 5
Apr 22 14:56:10 ubuntu kernel: [   35.631179] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
Apr 22 14:56:10 ubuntu kernel: [   35.631298] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
Apr 22 14:56:10 ubuntu kernel: [   35.631419] sata_nv 0000:00:08.0: Using ADMA mode
Apr 22 14:56:10 ubuntu kernel: [   35.631492] PCI: Setting latency timer of device 0000:00:08.0 to 64
Apr 22 14:56:10 ubuntu kernel: [   35.631607] scsi2 : sata_nv
Apr 22 14:56:10 ubuntu kernel: [   35.631679] scsi3 : sata_nv
Apr 22 14:56:10 ubuntu kernel: [   35.631849] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 16
Apr 22 14:56:10 ubuntu kernel: [   35.631896] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 16
Apr 22 14:56:10 ubuntu kernel: [   35.943498] ata3: SATA link down (SStatus 0 SControl 300)
Apr 22 14:56:10 ubuntu kernel: [   35.978509] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508d0000d6fa1d]
Apr 22 14:56:10 ubuntu kernel: [   36.254029] ata4: SATA link down (SStatus 0 SControl 300)
Apr 22 14:56:10 ubuntu kernel: [   36.254180] pata_amd 0000:00:06.0: version 0.3.10
Apr 22 14:56:10 ubuntu kernel: [   36.254251] PCI: Setting latency timer of device 0000:00:06.0 to 64
Apr 22 14:56:10 ubuntu kernel: [   36.254768] scsi4 : pata_amd
Apr 22 14:56:10 ubuntu kernel: [   36.254846] scsi5 : pata_amd
Apr 22 14:56:10 ubuntu kernel: [   36.255366] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
Apr 22 14:56:10 ubuntu kernel: [   36.255414] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
Apr 22 14:56:10 ubuntu kernel: [   36.259652] Driver 'sd' needs updating - please use bus_type methods
Apr 22 14:56:10 ubuntu kernel: [   36.259760] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Apr 22 14:56:10 ubuntu kernel: [   36.259814] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 14:56:10 ubuntu kernel: [   36.259859] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 14:56:10 ubuntu kernel: [   36.259915] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 14:56:10 ubuntu kernel: [   36.260000] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Apr 22 14:56:10 ubuntu kernel: [   36.260052] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 14:56:10 ubuntu kernel: [   36.260097] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 14:56:10 ubuntu kernel: [   36.260150] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 14:56:10 ubuntu kernel: [   36.260205]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
Apr 22 14:56:10 ubuntu kernel: [   36.340216] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 22 14:56:10 ubuntu kernel: [   36.343619] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 22 14:56:10 ubuntu kernel: [   36.746515] ata6.00: ATAPI: HL-DT-ST DVDRAM GSA-4160B, A306, max UDMA/66
Apr 22 14:56:10 ubuntu kernel: [   36.746702] ata6.01: ATA-7: SAMSUNG HD300LD, WK100-12, max UDMA/100
Apr 22 14:56:10 ubuntu kernel: [   36.746749] ata6.01: 586072368 sectors, multi 16: LBA48
Apr 22 14:56:10 ubuntu kernel: [   36.918181] ata6.00: configured for UDMA/66
Apr 22 14:56:10 ubuntu kernel: [   36.934250] ata6.01: configured for UDMA/100
Apr 22 14:56:10 ubuntu kernel: [   36.937987] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4160B A306 PQ: 0 ANSI: 5
Apr 22 14:56:10 ubuntu kernel: [   36.938096] scsi 5:0:0:0: Attached scsi generic sg1 type 5
Apr 22 14:56:10 ubuntu kernel: [   36.938180] scsi 5:0:1:0: Direct-Access     ATA      SAMSUNG HD300LD  WK10 PQ: 0 ANSI: 5
Apr 22 14:56:10 ubuntu kernel: [   36.938272] sd 5:0:1:0: [sdb] 586072368 512-byte hardware sectors (300069 MB)
Apr 22 14:56:10 ubuntu kernel: [   36.938326] sd 5:0:1:0: [sdb] Write Protect is off
Apr 22 14:56:10 ubuntu kernel: [   36.938370] sd 5:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Apr 22 14:56:10 ubuntu kernel: [   36.938426] sd 5:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 14:56:10 ubuntu kernel: [   36.938510] sd 5:0:1:0: [sdb] 586072368 512-byte hardware sectors (300069 MB)
Apr 22 14:56:10 ubuntu kernel: [   36.938562] sd 5:0:1:0: [sdb] Write Protect is off
Apr 22 14:56:10 ubuntu kernel: [   36.938606] sd 5:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Apr 22 14:56:10 ubuntu kernel: [   36.938659] sd 5:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 14:56:10 ubuntu kernel: [   36.938715]  sdb: sdb1 sdb2 < sdb5 >
Apr 22 14:56:10 ubuntu kernel: [   36.962850] sd 5:0:1:0: [sdb] Attached SCSI disk
Apr 22 14:56:10 ubuntu kernel: [   36.962912] sd 5:0:1:0: Attached scsi generic sg2 type 0

```

sda and sdb are inverted in the 2 runs...

---

### Post by bludo on 2008-04-22
I have no ideea. I haven't changed anything.

Here is what I've got..

---

### Post by ago on 2008-04-22
hmm "partion string 1" should be 10...

Boot with break=mount (always in verbose mode)

At the shell run

sed -i '/#!/ a set -x' /scripts/casper-premount/30custom_installation

The above appends "set -x" to /scripts/casper-premount/30custom_installation (you can check that by reading the top of the file with the command "head").

Then type "exit" to let the installation continue and post the logs as usual

---

### Post by bludo on 2008-04-22
Here it is

---

### Post by ago on 2008-04-22
hmm not sure it worked. basically did not get the extra info in the logs. we'll have to do it again.

delete the old logs

boot in verbose mode, make sure you have break=mount in the kernel line so that we stop at the right spot.

Then run the command in the previous post (watch the whitespaces!).

Then run

head /scripts/casper-premount/30custom_installation 

And check that the script starts with "set -x" as second line.

If all is good press exit to continue.

Thanks a lot, this is a critical bug that may delay ubuntu release, basically I suspect the issue is in the file above, adding set -x will provide some more debugging info.

---

### Post by cjwatson on 2008-04-22
These logs don't seem to have the set -x output from 30custom_installation, only from the rest of the initramfs. Are you sure you followed ago's instructions precisely? Were there any error messages when you did so?

(Thanks for all your help so far! I feel we're getting close.)

---

### Post by ago on 2008-04-22
Ops. You have to boot with break=mount not casper=mount. Sorry about that.

---

### Post by bludo on 2008-04-22
I had break=bottom added here :

kernel /ubuntu/install/boot/vmlinuz debug boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-i386.iso ro debug-ubiquity automatic-ubiquity locale=en_US.UTF-8 noprompt break=bottom --  


so I change it to break=mount? is it ok?

---

### Post by ago on 2008-04-22
Best way is to edit c:\ubuntu\install\grub\menu.lst

Within the block that has "Title Install in Verbose Mode"

Append "break=mount" to the line that starts with "kenrel..."

You should get to a shell BEFORE the brown screen with bird

---

### Post by ago on 2008-04-22
yeah you have to use break=mount and not break=bottom

---

### Post by bludo on 2008-04-22
Just to be sure. Do I still have to run sudo cp /custom-installation/preseed.cfg /var/log/ before the failure-command?

---

### Post by ago on 2008-04-22
> **bludo said:**
> Just to be sure. Do I still have to run sudo cp /custom-installation/preseed.cfg /var/log/ before the failure-command?

No need for that

---

### Post by bludo on 2008-04-22
Ok, now it hangs here after I've added this:

title Start installer in verbose mode

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debug boot=casper debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/hardy-desktop-i386.iso ro debug-ubiquity automatic-ubiquity locale=en_US.UTF-8 noprompt break=mount --  

initrd /ubuntu/install/boot/initrd.gz
boot

---

### Post by ago on 2008-04-22
Ok I think we nailed it! 

Well that was quite a debugging session you had! 
Thanks a lot for all your efforts, most helpful!
The fix should hopefully appear in the final release.

You deserve a hardy t-shirt :)

---

### Post by bludo on 2008-04-22
Great! I'm just natural at getting into bugs :)

I'm glad that I've been helpful. I'm looking forward towards the final release. I am considering the option of migrating my family onto ubuntu and that's why I wanted to give it a quick look.

Thanks!

---

### Post by ago on 2008-04-22
Bludo, one last effort, please follow the instructions here: [http://ubuntuforums.org/showthread.php?t=762695](http://ubuntuforums.org/showthread.php?t=762695)

The new initrd contains the fix (it is a i386 initrd, so use it only with i386 ISO! do not use it with AMD64). 

Pls let me know immediately if it works

---

### Post by bludo on 2008-04-22
I think the installation worked this time, but at the end, after it rebooted the computer and I choosed ubuntu, this is what I got:

Btw, I'm doing the installation from a mounted iso, not from a cd. Does it matter?

---

### Post by ago on 2008-04-22
1. uninstall any previous wubi installation, delete \ubuntu-backup
2. download the i386 ISO [http://releases.ubuntu.com/8.04/ubuntu-8.04-rc-desktop-i386.iso](http://releases.ubuntu.com/8.04/ubuntu-8.04-rc-desktop-i386.iso) and wubi 495 [http://wubi-installer.org/latest.php](http://wubi-installer.org/latest.php) and put them in the same folder
3. run Wubi but do not reboot
4. replace c:\ubuntu\install\initrd.gz with [http://people.ubuntu.com/~cjwatson/tmp/initrd-lupin-fix.gz](http://people.ubuntu.com/~cjwatson/tmp/initrd-lupin-fix.gz)
5. reboot and install normally
6. pls report immediately whether it works or not

---

### Post by bludo on 2008-04-22
That is exactly what I did and the installation worked I guess.. but see the previous screenshot.

---

### Post by ago on 2008-04-22
> **bludo said:**
> I think the installation worked this time, but at the end, after it rebooted the computer and I choosed ubuntu, this is what I got:

Btw, I'm doing the installation from a mounted iso, not from a cd. Does it matter?

This is after the second reboot (i.e. reboot after bird correct?).
I think the problem is that the disk order is almost random or your machine!
But that is a different issue. The installation was otherwise successful.
To fix it you have to change X = 0 <-> 1 in 

root (hdX,9) 

in /ubuntu/disks/boot/grub/menu.lst 
also edit the groot line

Even that might not be permanent if your disk order keeps changing

---

### Post by ago on 2008-04-22
Tip: you can edit things at boot on the fly by pressing esc to display the boot menu and then "e" to edit the first entry and "e" again to edit the root line.

Let me know if you can boot.

---

### Post by bludo on 2008-04-22
Yes, it works! I've edited the root line.

Thanks a lot!

---

### Post by ago on 2008-04-22
Bludo the new ISOs are out, they include the fix, and should work also with AMD64 without any need for special hacks. The issue with disk order will still be there, but it might be addressed by booting with "edd=on".

---

