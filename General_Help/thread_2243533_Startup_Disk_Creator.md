---
title: "Startup Disk Creator"
date: 2014-09-09
forum: General Help
---

### Post by uRock on 2014-09-09
Every time I try to create a bootable USB using Startup Disk Creator, it errors out. I captured this on video and uploaded it to Youtube here [https://www.youtube.com/watch?v=4q3q3H_9yJM&feature=youtu.be](https://www.youtube.com/watch?v=4q3q3H_9yJM&feature=youtu.be)

Any thoughts on what is going wrong and how to fix this?

Thanks for any and all help,
uRock

---

### Post by mc4man on 2014-09-09
S-d-c has been known to have issues when using it to erase. Maybe try first formatting in Disk Utility or whatever to Fat(32).
Here it now seems ok though I have replaced the current gnome-disk-utility in 14.04 (3.10.0-1ubuntu3 udisks2) with the[ much older 3.0.2-2ubuntu8,]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-tests") udisks/libgdu0

Though I just noticed S-d-c outright fails if I boot to a custom kernel, ok with the current 14.04 kernel.

Also enabling persistence can cause S-d-c to fail
(you'd think they'd get this app working good by now,...

Look at - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1318954](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1318954)
[https://bugs.launchpad.net/debian/+source/util-linux/+bug/1059872](https://bugs.launchpad.net/debian/+source/util-linux/+bug/1059872)
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1243365](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1243365)
or 100 others

---

### Post by uRock on 2014-09-09
Formatting to FAT first seems to have done the job. My thumb drives are usually EXT4.

Thanx!

Cheers & Beers,
uRock

---

