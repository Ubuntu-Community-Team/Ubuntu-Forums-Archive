---
title: "DVD drive won't eject"
date: 2008-05-04
forum: General Help
---

### Post by jessika-kaos on 2008-05-04
Still having an annoying problem with my DVD drive since I installed 8.04. It was working fine with 7.10, but now my DVD drive will sporadically refuse to eject. The only way I've found to get it to open is to reboot the computer. 

eject /dev/sda0 or eject /dev/cdrom0 do not work, nor does right clicking on the drive and selecting eject.

Any help would be appreciated.


 Also - I don't know if this might be related, but the system's logs are filled up with entries like this, repeated about every 30 seconds:

```
May  4 01:38:49 HIVE kernel: [  884.223789] ata4.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
May  4 01:38:49 HIVE kernel: [  884.223800] ata4.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
May  4 01:38:49 HIVE kernel: [  884.223801]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
May  4 01:38:49 HIVE kernel: [  884.223802]          res 40/00:03:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
May  4 01:38:49 HIVE kernel: [  884.223804] ata4.01: status: { DRDY }
May  4 01:38:49 HIVE kernel: [  884.223822] ata4: soft resetting link
May  4 01:38:49 HIVE kernel: [  884.880199] ata4.00: configured for UDMA/25
May  4 01:38:50 HIVE kernel: [  885.004146] ata4.01: configured for UDMA/33
May  4 01:38:50 HIVE kernel: [  885.004157] ata4: EH complete
```

---

### Post by scouser73 on 2008-05-04
> **jessika-kaos said:**
> Still having an annoying problem with my DVD drive since I installed 8.04. It was working fine with 7.10, but now my DVD drive will sporadically refuse to eject. The only way I've found to get it to open is to reboot the computer. 

eject /dev/sda0 or eject /dev/cdrom0 do not work, nor does right clicking on the drive and selecting eject.

Any help would be appreciated.


 Also - I don't know if this might be related, but the system's logs are filled up with entries like this, repeated about every 30 seconds:

```
May  4 01:38:49 HIVE kernel: [  884.223789] ata4.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
May  4 01:38:49 HIVE kernel: [  884.223800] ata4.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
May  4 01:38:49 HIVE kernel: [  884.223801]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
May  4 01:38:49 HIVE kernel: [  884.223802]          res 40/00:03:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
May  4 01:38:49 HIVE kernel: [  884.223804] ata4.01: status: { DRDY }
May  4 01:38:49 HIVE kernel: [  884.223822] ata4: soft resetting link
May  4 01:38:49 HIVE kernel: [  884.880199] ata4.00: configured for UDMA/25
May  4 01:38:50 HIVE kernel: [  885.004146] ata4.01: configured for UDMA/33
May  4 01:38:50 HIVE kernel: [  885.004157] ata4: EH complete
```

On your drive there should be a tiny hole, big enough for a pin/unfolded paper clip to slide in and thus ejecting the drawer.

Hope this helps.

---

