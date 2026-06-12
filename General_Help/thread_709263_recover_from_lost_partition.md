---
title: "recover from lost partition"
date: 2008-02-27
forum: General Help
---

### Post by Dithers on 2008-02-27
I have a week old install of gutsy that was working beautifully. I decided to install wine just to check it out since I haven't played with it yet and the next morning I got a grub 17 error. I tried everything I could find to fix it before giving up and decided to install again in free space to try and recover 1 file before reinstalling for real again.

I don't have my sudo fdisk to paste but I now have 5 partitions on 1 hd

sda1 I believe to be a win/recovery partition that was on from before
sda2 should be my old linux partition but it comes up as extended now
a new linux partition and two swaps

I would like to  mount sda2 so I can retrieve the file before starting over but its not working

any suggestions

---

### Post by az on 2008-02-27
> **Dithers said:**
> I have a week old install of gutsy that was working beautifully. I decided to install wine just to check it out since I haven't played with it yet and the next morning I got a grub 17 error. I tried everything I could find to fix it before giving up and decided to install again in free space to try and recover 1 file before reinstalling for real again.

I don't have my sudo fdisk to paste but I now have 5 partitions on 1 hd

sda1 I believe to be a win/recovery partition that was on from before
sd2 should be my old linux partition but it comes up as extended now
a new linux partition and two swaps

I would like to  mount sda2 so I can retrieve the file before starting over but its not working

any suggestions

If partition 2 is extended, then look for the other partition within the extended one.  Try mounting the partition that's listed as a linux partitin.

---

