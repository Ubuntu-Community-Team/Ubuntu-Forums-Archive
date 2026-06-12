---
title: "I need help with grub error 22 / partition screwup"
date: 2007-02-27
forum: General Help
---

### Post by oranguman on 2007-02-27
n an effort to remove my windows partition and make ubuntu my primary, I moved the ubuntu partition via gparted's copy and paste, to make it start at 0 bytes and take up the whole disk..

in retrospect, I guess it is asking a bit much to have grub magically find this out and boot up as before.. I get 'error 22' on boot and that's that.

I need to know how to point grub toward the new partition for booting, the correct one being flagged in my fdisk output below as 'boot'.

"ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4762 38250733+ 83 Linux
/dev/hda3 4763 4864 819315 5 Extended
/dev/hda5 4763 4864 819283+ 82 Linux swap / Solaris
"

i'm here watching the thread so ask away.

and thanks for your time!

---

### Post by oranguman on 2007-02-27
really sorry to double-post this issue but I was very desperate for an hour or so... almost chucked my computer at my television set, thereby eliminating two problems at once


anyway, I fixed my problem without reformatting. I just had to reinstall GRUB. if you are having a similar problem, check out the original post and the other thread it references. 

find the original post here: [http://www.ubuntuforums.org/showthread.php?p=2223104#post2223104](http://www.ubuntuforums.org/showthread.php?p=2223104#post2223104)

---

