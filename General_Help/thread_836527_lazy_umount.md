---
title: "lazy umount"
date: 2008-06-21
forum: General Help
---

### Post by geo909 on 2008-06-21
Hi,

I often use the -l option to umount (that is "lazy" umount)
when my device is busy. Although i have read the man entry for this, I can't get what it means..

 can someone explain me in plain words?

Thanks!

---

### Post by drs305 on 2008-06-21
From the umount man page:
[B]-l Lazy  unmount.  Detach the filesystem from the filesystem hierarchy now, and cleanup all references to the filesystem as soon as it is not busy anymore.  (Requires kernel 2.4.11 or later.)
[/B]

So it unmounts and takes care of the housecleaning as time permits.

---

### Post by geo909 on 2008-06-21
So why not to do something like this by default?

---

### Post by drs305 on 2008-06-21
> **geo909 said:**
> So why not to do something like this by default?

My guess is that while us normal users may be mounting relatively small partitions/devices that don't take long to unmount, linux is designed to accommodate extremely large devices which are connected for long periods of time. Such a situation might require a long time to put the system files in order during un-mounting. The longer the time period, the longer bad things could happen while this is happening.  

Just a guess.

---

### Post by chenxing on 2008-11-06
You may have a look at [http://aplawrence.com/Linux/lazy-unmount.html](http://aplawrence.com/Linux/lazy-unmount.html)

or [http://www.linux-wiki.cn/index.php/Umount](http://www.linux-wiki.cn/index.php/Umount) if you could read Chinese.

"Lazy umount" is not as safe as you thought of.So I don't think lazy umount a good choice to eject USB sticks.

---

