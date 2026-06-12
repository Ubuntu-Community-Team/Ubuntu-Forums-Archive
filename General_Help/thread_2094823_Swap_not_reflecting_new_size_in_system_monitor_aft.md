---
title: "Swap not reflecting new size in system monitor after resizing swap partition"
date: 2012-12-14
forum: General Help
---

### Post by Pollox on 2012-12-14
I increased the size of my swap partition (using GParted) from 2.6GiB to 5.09GiB. System monitor still shows the old, smaller size, although GParted shows the new size. How do I fix this? The swap partition otherwise seems to be working fine.

---

### Post by bhaveshnande on 2012-12-15
I think you must try turning the swap off and on again with
```
sudo swapoff -a
```
and
```
sudo swapon -a
```
then later check the amount of total swap with 
```
free -m
```

---

### Post by Pollox on 2012-12-15
Thanks for the idea, but no luck there. Swap still shows as 2667 MiB from the free command.

---

### Post by Pollox on 2012-12-15
More information that may be helpful:
```
sudo swapon -a --verbose
swapon on /dev/sda3
swapon: /dev/sda3: found swap signature: version 1, page-size 4, same byte order
swapon: /dev/sda3: pagesize=4096, swapsize=2796593152, devsize=5464129536

```

The swapsize still shows the old size, but the devsize shows the new size. So I just need to figure out where that swapsize value comes from and update it.

---

### Post by Pollox on 2012-12-15
Fixed it! Here's what I did in case anyone else has this issue:
```
$sudo swapoff -av
swapoff on /dev/sda3
$ sudo mkswap /dev/sda3
Setting up swapspace version 1, size = 5336060 KiB
no label, UUID=9cd590ef-0e98-4592-80b8-1716551f5a75
```
Then I opened /etc/fstab and edited the UUID below the line "# swap was on /dev/sda3 during installation" to match the UUID outputted by mkswap.

Finally, turned the swap back on and everything worked:
```
$ sudo swapon -a --verbose
swapon on /dev/sda3
swapon: /dev/sda3: found swap signature: version 1, page-size 4, same byte order
swapon: /dev/sda3: pagesize=4096, swapsize=5464129536, devsize=5464129536
```

Maybe I should have just deleted the swap partition and made a new one rather than moving and resizing it.

---

