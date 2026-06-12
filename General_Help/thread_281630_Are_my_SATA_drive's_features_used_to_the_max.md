---
title: "Are my SATA drive's features used to the max?"
date: 2006-10-21
forum: General Help
---

### Post by Theimon on 2006-10-21
My current set-up is: 1 Maxtor 250GB SATA disk which is partitioned. First few partitions are for Ubuntu and its swap and /boot. One partition for data. Along the SATA drive are 2 PATA drives for data only.
Installation of Ubuntu 6.06 with kernel 2.6.15-27-k7 on the /dev/sda went with no trouble at all. Ubuntu recognizes the drive and read/write actions are done without a pain except.....it seems slow. Speeds are not SATA "worthy".
So I took out sdparm to see if I could get some info on the disk and this is what it tells me:
```

theimon@theimon:/$ sudo sdparm --long /dev/sda
Password:
    /dev/sda: ATA       Maxtor 6L250S0    BACE
    Direct access device specific parameters: WP=0  DPOFUA=0
Read write error recovery mode page:
  AWRE        1  Automatic write reallocation enabled
  ARRE        1  Automatic read reallocation enabled
  PER         0  Post error
Caching (SBC) mode page:
  WCE         1  Write cache enable
  RCD         0  Read cache disable
Control mode page:
  SWP         0  Software write protect

```

It's a PATA drive?? That's not looking good.
Maybe someone has some suggestions on this matter? Help would be much appreciated.

---

### Post by Theimon on 2006-10-23
Subtle bump.......

---

### Post by Coelocanth on 2006-10-23
Do you mean you're reading and writing data between the SATA and the PATA drives? If so, that may be your bottleneck, as the system is only as fast as the slowest component.

As for it saying it's a PATA drive: I don't see that. It's identifying your drive as sda, which means it's not thinking it's a PATA drive (or it would be identified as hda instead), if I understand things correctly. Of course, being fairly new to Linux, I could be wrong on this.

---

### Post by Theimon on 2006-10-23
What I mean is: Is Ubuntu using the SATA features to their maximum (higher data bandwidth etc.) or is SATA support on Linux still in such a phase that it will use SATA disks almost equivalent to PATA disks regarding speed and/or commands. 
It feels like the reaction time when performing read/write actions on the SATA drive and the PATA drives don't differ that much.
I'm not talking about actions from SATA to PATA or vice versa, I know it will narrow down speed to its slowest component. I'm talking purely actions on the same disk and therefore my Ubuntu system speed in particular as it is on my SATA drive. It feels like Ubuntu is slower on my SATA drive then Windows used to be when it was on my SATA drive. (or could the speed issue be caused by ext3? meaning ext3 is a "slower" fs than NTFS? just guessing here...)

---

### Post by Ramses de Norre on 2006-10-23
Speed test: ```
sudo hdparm -tT /dev/???
```
And the drive your OS runs from will be negatively influenced by this fact so to get accurate values you should perform this tests from a live disc without swap being used on the tested drives.

---

