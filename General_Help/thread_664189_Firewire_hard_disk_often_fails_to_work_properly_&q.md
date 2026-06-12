---
title: "Firewire hard disk often fails to work properly: &quot;Node changed&quot; reported on dmesg"
date: 2008-01-10
forum: General Help
---

### Post by wirawan0 on 2008-01-10
I have a triple interface Western Digital My Book, which worked fine under USB2 interface. However, with the firewire interface, the harddisk often "stops" working by itself. Here's an excerpt of dmesg output:

```

[74977.716000] ieee1394: sbp2: Logged into SBP-2 device
[74977.740000] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[74977.860000] scsi 1:0:1:0: Enclosure         WD       My Book Device        PQ: 0 ANSI: 4
[74977.860000] scsi 1:0:1:0: Attached scsi generic sg1 type 13
[75076.660000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[75076.660000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0090a9769166fc2c]
[75076.664000] sd 0:0:0:0: [sda] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[75076.664000] end_request: I/O error, dev sda, sector 12423
[75076.664000] Buffer I/O error on device sda1, logical block 1545
[75076.664000] lost page write due to I/O error on sda1
[75076.664000] Buffer I/O error on device sda1, logical block 1545
[75076.664000] lost page write due to I/O error on sda1
[75076.664000] Buffer I/O error on device sda1, logical block 1545
[75076.664000] lost page write due to I/O error on sda1
[75076.664000] Buffer I/O error on device sda1, logical block 0
[75076.664000] lost page write due to I/O error on sda1

```

Here's the sequence of things:

* I plugged in the firewire cable to the laptop, and the hard disk was recognized with  /media/wdbook mountpoint -- that's fine

* I tried to unmount using `sudo umount /media/wdbook' ; it seemed to unmount fine, so I unplugged the firewire cable.

* When I replug the harddrive onto another laptop with USB2, it would not mount. dmesg has error: 

```

[1141573.836000] JBD: no valid journal superblock found
[1141573.836000] EXT3-fs: error loading journal.

```

The journal seemed to have been destroyed. I had to use e2fsck to remove the journal, fixed a number of errors, and recreate the journal. Anyway, the harddrive seemed to be fine now.

But I still have a nagging question concerning the reliability of firewire connection on my first laptop. IT is a SONY VAIO, with i.Link connection (it's basically a 4-pin firewire). So I used 4-pin  to 6-pin cable to connect to the external harddrive.

Has anybody known better about firewire external hard drive with Ubuntu Linux? How reliable is it, and what are the known issues? USB2 seems to be the safest way for now, but the VAIO laptop was old enough to not have its own USB2 port. If I can't reliably use the HDD with firewire, that really defeats the purpose of having the triple interface here.

I was able to connect a SONY camcorder via firewire to fetch the DV tape data--that was perfectly fine. So I don't think HDD should be an issue. But this experience caused me to doubt, really.

The OS is Ubuntu 7.10, by the way.

Wirawan

---

