---
title: "Performance Tweaking XFS"
date: 2007-08-14
forum: General Help
---

### Post by V3lier on 2007-08-14
Well I am trying to do the performance tweaking for XFS by following the instructions in [this]("http://everything2.com/index.pl?node_id=1479435") website but when I run "sudo hdparm -c3 -d1 -u1 /dev/hda" it tells me "hdparm -c3 -d1 -u1 /dev/hda". What directory am I supposed to use? I have three partitions:

 /dev/sda1 XFS /
/dev/sda2 ext3 /boot
/dev/sda3 linux-swap

I tried changing "/dev/hda" to "/dev/sda1" but it doesn't work. It gives me this:

/dev/sda1:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 setting unmaskirq to 1 (on)
 HDIO_SET_UNMASKINTR failed: Inappropriate ioctl for device
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 IO_support   =  0 (default 16-bit)

I don't know what directory to use. Help would be greatly appreciated.

---

### Post by V3lier on 2007-08-14
*bump*

---

### Post by V3lier on 2007-08-14
*bump*

---

### Post by dabl on 2007-08-14
You may need to use sdparm, rather than hdparm, if your drives are listed in /etc/fstab as sd*.  You can learn the capabilities of either of them with ```
man hdparm
``` or ```
man sdparm
```

---

### Post by V3lier on 2007-08-14
Thank you for the response. I'm wondering if there is a way to turn the sda to hda? It seems most people have hda and I have different. I don't understand why I have sda instead.

---

### Post by V3lier on 2007-08-14
*bump*

---

### Post by V3lier on 2007-08-14
*bump*

---

### Post by cwhamsun on 2007-09-18
sda is used for scsi or sata drives and I think the newer kernel and/or ubuntu versions use sda for ide pata drives also. On my laptop ubuntu feisty calls the only drive sda while gentoo calls it hda. It is an ide pata drive. Some hdparm functions will work on either hda or sda, like the speed tests -t or -T. The new driver for sata and some pata drives is called libata. This page here should answer the question about the exact parameters you tried to set. [http://linux-ata.org/faq.html](http://linux-ata.org/faq.html) That relates to the driver, if you have a sata drive I am not even sure if all of the parameters you are trying to tweak even apply. Also as explained on that page some of those parameters may not even be relevent. Try hdparm -tT /dev/hda to test your drive speeds. I would do it 2 or three times to get a better idea. Reading that page on tweaking you mentioned, he shows that changing those parameters with hdparm made his buffered disk read go from 4.2 M/s to 40.25 M/s. It looks like that page is a few years old, and I don't think newer ide pata or would get that kind of jump up. The newer drivers and kernels get that speed untweaked. I have an old gateway and with two old western digital hard drives. One is 40gb and one is 30gb and they seem to be the same model except for the size. The 30gb only gets 20M/s but the 40gb gets 40+M/s. For comparison here are results on my newer machines.
sempron (socket a) 2ghz 1g ram
western digital 250gb sata drive with 8mb buffer
dev/sda:
 Timing cached reads:   660 MB in  2.00 seconds = 329.82 MB/sec
 Timing buffered disk reads:  170 MB in  3.01 seconds =  56.49 MB/sec
seagate 80gb ide pata drive with 8mb buffer
dev/hda:
 Timing cached reads:   696 MB in  2.00 seconds = 347.97 MB/sec
 Timing buffered disk reads:  168 MB in  3.04 seconds =  55.34 MB/sec

two different drives roughly the same scores. tweaking filesystems and mount options and drive parameters will probably not change the numbers very much on those tests. try the bonnie++ tests on your system to compare your numbers to his. The drive itself will make a drastic improvement. Here is a western digital raptor 74gb sata 8mb buffer on my other machine which is about the same cpu and ram
athlonxp 2ghz 1g ram
dev/sda:
 Timing cached reads:   836 MB in  2.00 seconds = 417.11 MB/sec
 Timing buffered disk reads:  254 MB in  3.02 seconds =  84.16 MB/sec


those vary some by partition and file system used but not by much.

Since that tweaking page is older I doubt you can change those parameters and get the kind of increase he did. newer hard drives/kernel/drivers and xfs versions will probably be much more tweaked by default. If you really want to increase your speed a raptor drive shows the obvious increase., and it is an older raptor, the newer 74gb and 150gb are faster than the one I have. They are really expensive compared to other drives but the difference is clear. 10,000 rpm drive vs 7200rpm drive is a huge difference. getting two regular drives and running some raid can outperform a raptor and is cheaper also. but raid 0 risks your data. If you have the money get a raptor for the drive your os is on.

---

