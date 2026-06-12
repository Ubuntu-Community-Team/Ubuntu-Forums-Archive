---
title: "I screwed up my mbr"
date: 2007-01-05
forum: General Help
---

### Post by Naddiseo on 2007-01-05
Hi, so today I reluctantly installed Xp on a spare partition (because wine was being a little bia**) but it overwrote my boot table, so I used a live CD to reinstall it.. but I think I reinstalled it wrong because when I boot and select the XP option it just loads up grub again. I think I installed grub in two places.

My partitions are as follows:
hdc1 - ext3, 230GB of storage
hdc2 - ntfs, 20GB for my XP. I htink I may have installed grub on here
hdd1 - ext3, 36GB for edgy, my main partition that I boot off
hdd2 - swap 2gb.

and my menu.lst on hdd1
```

title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot 

```

How do I boot into XP/restore my access to it?

---

### Post by ~LoKe on 2007-01-05
You're going to want to screw with hd(0,1) by changing it to hd(2,0), hd(0,2), etc.  I don't know if there's a right way to do this or not.

---

