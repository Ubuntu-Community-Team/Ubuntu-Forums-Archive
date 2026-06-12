---
title: "Can not write to /dev/sdc, not a directory"
date: 2017-02-12
forum: General Help
---

### Post by chrisjimbo on 2017-02-12
Hi All,

I am having a problem writing three Debian .iso's to a USB.

I have attempted 

sudo cp debian-8.7.1-amd64-DVD-1.iso debian-8.7.1-amd64-DVD-2.iso debian-8.7.1-amd64-DVD-3.iso /dev/sdc

And I get 

cp: target '/dev/sdc' is not a directory

Debian directs you to unmount the USB, and input the above into the terminal.

Have attempted on ext4, FAT32, and unallocated. 

I have also tried /dev/sdc1, I get a similar error.

Am I being thick? Did I miss something?

Thanks in advance for your help!

---

### Post by lisati on 2017-02-12
Duplicate of [https://ubuntuforums.org/showthread.php?t=2352451](https://ubuntuforums.org/showthread.php?t=2352451)

---

