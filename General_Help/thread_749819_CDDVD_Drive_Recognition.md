---
title: "CD/DVD Drive Recognition"
date: 2008-04-08
forum: General Help
---

### Post by emobuddy88 on 2008-04-08
I've only been using Ubuntu for a few days now. But before I had converted from Vista, I saved files that I wanted to keep on DVD-R's. But I have reached the same problem that many people has, which is the CD drive won't work. I looked here at the forums and at several other help guides and forums, but none helped. I receive the message of:

[B][INDENT]Cannot mount volume.

Invalid Mount option when attempting to mount the volume 'UDF Volume'.[/INDENT][/B]

Any help on how I can get this to work?

---

### Post by emobuddy88 on 2008-04-08
Please, I desperately need help, I don't want to switch back to windows :(

---

### Post by prshah on 2008-04-08
> **emobuddy88 said:**
> 
[B][INDENT]Cannot mount volume.
Invalid Mount option when attempting to mount the volume 'UDF Volume'.[/INDENT][/B]


Any relevant dmesg output would be helpful:```
dmesg | grep -i -A 3 -B 3 cdrom
``` or ```
dmesg | grep -i -A 3 -B 3 sr0
```

---

### Post by emobuddy88 on 2008-04-09
That's what it gave me

[INDENT]jacob@Toxicity:~$ dmesg | grep -i -A 3 -B 3 sr0
[   23.773470] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   23.780538] ata3.00: configured for UDMA/133
[   23.947129] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-2 05.0 PQ: 0 ANSI: 5
[   23.969099] sr0: scsi3-mmc drive: 62x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.969104] Uniform CD-ROM driver Revision: 3.20
[   23.969299] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   23.973345] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   23.973365] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   23.987228] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[/INDENT]

---

