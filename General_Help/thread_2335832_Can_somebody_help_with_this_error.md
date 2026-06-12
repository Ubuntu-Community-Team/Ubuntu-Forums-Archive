---
title: "Can somebody help with this error?"
date: 2016-09-01
forum: General Help
---

### Post by guliver on 2016-09-01
After power went off my Ubuntu does not start anymore...

Can anybody help?

---

### Post by Jimysbil on 2016-09-01
Try to boot in recovery mode (with network) and type those commands:
```
sudo apt-get install --reinstall xserver-xorg
reboot
```

---

### Post by cariboo on 2016-09-01
Boot from a live CD or usb, open a terminal and type:

```
sudo fdisk -l
```

to determine which partition / is on, for example on my laptop the result of the command looks like this:

```
Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: E3B1E025-5431-11E5-8B71-F8C7AF01A0CC

Device          Start        End   Sectors   Size Type
/dev/sda1        2048    2099199   2097152     1G Windows recovery environment
/dev/sda2     2099200    2303999    204800   100M EFI System
/dev/sda3     2304000    2566143    262144   128M Microsoft reserved
/dev/sda4     2566144  827933044 825366901 393.6G Microsoft basic data
/dev/sda5  1442334720 1443950591   1615872   789M Windows recovery environment
/dev/sda6  1443951226 1465147392  21196167  10.1G Windows recovery environment
/dev/sda7   827934720  866995266  39060547  18.6G Linux filesystem
/dev/sda8   866996224  874809343   7813120   3.7G Linux swap
/dev/sda9   874809344 1442334719 567525376 270.6G Linux filesystem

Partition table entries are not in disk order.
```

in my case, / is on /dev/sda7. Once you determine on which partition / is located (for the sake of this post I'll use my / location) type the following command:

```
sudo fsck /dev/sda7
```

let fsck do it's thing, and once finished, reboot to see if the problem has been repaired.

---

### Post by guliver on 2016-09-01
I started FSCK to all partitions from Recovery Mode, its stuck at sda1 (1.2% non-contiguous) for almost 2 hours... I did not interrupt it... its still doing...

---

### Post by Jimysbil on 2016-09-01
As long as fsck is correcting errors you should let it until it finish.Even if a package is corrupted unfortunately you have to fix your partition first.

---

### Post by ajgreeny on 2016-09-02
> **guliver said:**
> I started FSCK to all partitions from Recovery Mode, its stuck at sda1 (1.2% non-contiguous) for almost 2 hours... I did not interrupt it... its still doing...
Do you have any Windows partitions on the disk that you are running FSCK on?
FSCK is a tool for Linux partitions only and I do not know what might happen to a Windows partition if used on it so do not interrupt the job until someone else has given you a hopefully better answer than I can.

---

### Post by guliver on 2016-09-02
This is Linux partition. Its been running all night, no change, still stuck at 1.2%.


?????

---

### Post by guliver on 2016-09-02
Fixed!

Followed this tutorial
[http://punygeek.blogspot.com/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html](http://punygeek.blogspot.com/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html)

however, i recommend using vim for all editing because for some reason direct commands did not make change to the files...

After fixing swap I had no internet problem as well. Figured out network adapter was dead. It was listed as active but no internet. When LAN cable was plugged in my routers LED did not show any light. I figured out that lightning strike the other day probably damaged it.

Installed different one, did some changes in network files and its working fine.

Thanks guys

---

