---
title: "automatically mount external WD hard drive at boot"
date: 2013-02-28
forum: General Help
---

### Post by associates on 2013-02-28
Hi,

I'm still new to Ubuntu. I am trying to mount my external Western Digital MyBook HDD automatically to my Ubuntu Server 12.04 LTS at the boot time.

what I'm concerned is the type of format I need to add to my /etc/fstab. afraid that I may stuff up the format of my external HD.

Here is the output  when I run "mount"
<snip>
/dev/sdb1 on /media/mybook type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

I'm wondering if I do the right thing by adding the following entry to my /etc/fstab

/dev/sdb1  /media/MyBook   fuseblk  auto,user,rw,exec  0  0 

Any help would be greatly appreciated.

Thank you

---

