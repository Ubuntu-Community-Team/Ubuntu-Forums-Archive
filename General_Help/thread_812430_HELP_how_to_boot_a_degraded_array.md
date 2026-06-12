---
title: "HELP how to boot a degraded array"
date: 2008-05-29
forum: General Help
---

### Post by ASULutzy on 2008-05-29
Hey all, I recently had a disk fail in my software RAID 1. I can still boot to Windows, but if I choose to boot into Ubuntu it falls back to a busybox prompt. I've tried changing the root= from the current UUID to /dev/md0 with the same results.

I have a live-usb and am able to boot off that, but am not really 100% sure what I should actually do to enable Ubuntu to boot the degraded array until I can buy another hdd to replace and rebuild the array.

Please help, the last couple of days of only having Windows on my desktop (thank god for my Ubuntu laptop) have been a real torture.

Thanks so much!

---

### Post by ASULutzy on 2008-05-29
I tried mdadm --assemble /dev/md0 /dev/sdc1 and it said that /dev/sdc1 didn't have a valid superblock?

when I do cat /proc/partitions I see /dev/sdc1 but /dev/md0 isn't there. That's also why it falls to busybox, says /dev/md0 doesn't exist.

When I boot from live-usb I can see /dev/md0; it's a degraded array.

Help me forum! :P

edit: so I found a solution... [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136225](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136225)

lol, anyone got a better idea till I get a new disk?

---

### Post by ASULutzy on 2008-05-30
bump before bed as this is an issue that ought to have a simple fix and the fact that scouring the net and forums provides no help is very odd to me...

What's the point of RAID-1 if you can't boot a degraded array by default in Ubuntu?

---

### Post by ASULutzy on 2008-05-30
morning bump?

---

### Post by ASULutzy on 2008-05-30
lunch bump

---

