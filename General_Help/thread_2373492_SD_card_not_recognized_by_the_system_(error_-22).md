---
title: "SD card not recognized by the system (error -22)"
date: 2017-10-06
forum: General Help
---

### Post by benjamin-loubet on 2017-10-06
Hello,

I have been given a 16 GB micro SD card by a colleague to help her take back her data. It is not recognized neither on Windows or Mac so I told her I could see what I could do for her with Ubuntu. Unfortunately, it is not automatically mounted. Thus I try to mount it manually and type ```
sudo fdisk -l
``` which only prints out the partitions of my laptop.
Then I just typed ```
tail -f /var/log/syslog
``` and plugged my SD card which gave me more information:

```
Oct  6 19:31:12 bsl-EasyNote-TSX66HR kernel: [35783.693133] mmc0: unrecognised CSD structure version 3
Oct  6 19:31:12 bsl-EasyNote-TSX66HR kernel: [35783.693148] mmc0: error -22 whilst initialising SD card
Oct  6 19:31:12 bsl-EasyNote-TSX66HR kernel: [35783.871355] mmc0: unrecognised CSD structure version 3
Oct  6 19:31:12 bsl-EasyNote-TSX66HR kernel: [35783.871371] mmc0: error -22 whilst initialising SD card
Oct  6 19:31:12 bsl-EasyNote-TSX66HR kernel: [35784.051589] mmc0: unrecognised CSD structure version 3
Oct  6 19:31:12 bsl-EasyNote-TSX66HR kernel: [35784.051605] mmc0: error -22 whilst initialising SD card
Oct  6 19:31:12 bsl-EasyNote-TSX66HR kernel: [35784.231742] mmc0: unrecognised CSD structure version 3
Oct  6 19:31:12 bsl-EasyNote-TSX66HR kernel: [35784.231757] mmc0: error -22 whilst initialising SD card
```

Now then, is it all I can do for her? Is her SD Card dead?

I stay at your disposal if you need any other information and thanks for any help you can give :)

---

### Post by ajgreeny on 2017-10-06
As fdisk didn't find it the disk may be dead, as you suspect.

Have a look at it (if it's seen) in the Disks utility of your Ubuntu and if it is seen run the smart tools on it to see what errors are shown.

---

### Post by efflandt on 2017-10-07
You might try a USB card reader in case the card is one that the mmc device cannot handle. USB drivers may be more universal than more specific mmc drivers. Although, it would have to be a rather old laptop to not handle SD/microSD 4 GB to 32 GB (SDHC). And in the end, it may just give you more confirmation that it is dead.

---

### Post by benjamin-loubet on 2017-10-07
Thanks for your quick answers,

Disk Utility doesn't see the SDcard and since my laptop is not that old, I think the dead SDcard idea must be the good one...

I mark the thread as solved, thank you again !

---

