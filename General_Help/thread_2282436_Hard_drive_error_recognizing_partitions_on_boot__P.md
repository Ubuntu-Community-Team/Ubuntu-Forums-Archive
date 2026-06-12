---
title: "Hard drive error recognizing partitions on boot / Possible Fake Raid Problem"
date: 2015-06-14
forum: General Help
---

### Post by excetara2 on 2015-06-14
I get an error on the boot that I took a screen shot below. Also the output of the fdisk -l command is shown. sda: unkwown partition table is the error. And then conflicting device mode. I think something got screwed up in my fake raid but windows still boots and works fine recognizing all partitions including the linux partitions. Could something have got messed up in /etc/fstab?

I am running Ubuntu 15.04 on an Asus UX301 dual boot with windows 8. The internal drive is ran as a raidx0 with two 256GB drives.

[http://i.stack.imgur.com/S3Cb5.jpg](http://i.stack.imgur.com/S3Cb5.jpg)

[http://i.stack.imgur.com/EVbnk.jpg](http://i.stack.imgur.com/EVbnk.jpg)

---

### Post by Steve_Horan on 2015-06-14
This has been an issue with udev and device mapper for some time. These "fake raid" devices are no good in the current implementation of udev. There are multiple bug reports for this. The only fix action I have seen is move the root volume group to a different drive..

---

### Post by wildmanne39 on 2015-06-14
Please use thumbnails or url's when posting images, there are people that have slow connections that have trouble loading pages with large images.

---

