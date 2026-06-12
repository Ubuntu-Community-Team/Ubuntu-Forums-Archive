---
title: "How long is mdadm --grow critical?"
date: 2013-01-29
forum: General Help
---

### Post by Blogem on 2013-01-29
Hello,

I'm currently growing my software RAID 5 set with an extra drive, going from 4 to 5 drives (I'm using mdadm --grow). I've done this before and always unmounted the filesystem, just to be on the safe side. However, I have no idea what the risks are if I would use the filesystem while growing.

I've read on several places that the initial part of growing is critical (presumably the 128K part?), but it's not clear to me how much risk is involved in the next part. For instance: if a drive would fail right now (during the grow), would I loose my full RAID? Or does it function right now as a RAID 5 set with 4 drives (as it was before I started the grow)?

An explanation or links to an explanation on this would be awesome, I was unable to find it.

---

### Post by SaturnusDJ on 2013-01-29
While I was going from raid1 to raid5, I was able to access data at all time. Especially during grow it should be possible because that's not the filesystem.

The question about a drive failing is interesting. I assume roll back is possible and otherwise at most a degraded array as result, no data loss. I'll try to find out with a VM.

Do you have links to those 'several places?'

---

### Post by Blogem on 2013-01-29
Thanks for your reply!

> **SaturnusDJ said:**
> While I was going from raid1 to raid5, I was able to access data at all time. Especially during grow it should be possible because that's not the filesystem.

The question about a drive failing is interesting. I assume roll back is possible and otherwise at most a degraded array as result, no data loss. I'll try to find out with a VM.

I know you can mount the filesystem, however I'm worried of the problems it might cause. The actual mounting won't be an issue, but if I would accidentally corrupt the filesystem or cause a drive the fail, it might pose a problem. Doing more stuff on the drives will probably heighten the risk of it failing.

The question is thus mainly: what happens when a drive fails during an mdadm --grow (specifically of a RAID 5). I was unable to find anything on this, it would be cool if you're able to test it.

> Do you have links to those 'several places?'
Best source imo: [https://raid.wiki.kernel.org/index.php/Growing](https://raid.wiki.kernel.org/index.php/Growing)

---

### Post by Blogem on 2013-01-29
Just answered my own question with the URL, must have missed that part while digging through the docs: > It is also important to note that while the array undergoes the resync process, it is vulnerable to irrecoverable failure if another drive were to fail.

So I'm just going to leave it alone for now... No need to make any more dangerous.

EDIT: I must read better, this is afaik concerning the replacement of drives, not adding drives..

---

### Post by SaturnusDJ on 2013-01-30
Here's my experience so far:

Raid5, 3 drives --> 4 drives

When the new drive or a current drive of the array that's being expanded (--grow) fails...the process halts or continues. Anyways: you'll have a degraded array.

Again I must make an assumption:
A part of the data is on the new drive, depending on where in the process (..%) one of the drives failed.

What you want to do now is roll back to (in my case) raid5 with 3 drives.
```
mdadm --grow /dev/md0 --raid-devices=3
```
Most likely it will say: "use --grow --array-size first to truncate array." followed by an example containing probably the right value.
The right value can be obtained by running:
```
mdadm --detail /dev/md0
```
Take the "Used Dev Size" and multiply by the amount of devices that will be left in a non-degraded array minus one. In my example: 511488*(3-2)=1022976.

Command will be:
```
mdadm --grow /dev/md0 --array-size=1022976
```
And now:
```
mdadm --grow /dev/md0 --raid-devices=3 --backup-file=/mnt/usbdrive/file
```
The backup-file is mandatory for a negative grow (shrink) and should not be places on the array that's being resized.

Reshape and recovery follow.


When a drive disconnects during the negative grow (shrink), things are bad. It's game over when it died. When it's still alive the backup-file might be the only way to restore the array.

I'll post again when I know more.

---

### Post by Blogem on 2013-01-30
Really cool that you're looking this far into it. Bedankt!

> **SaturnusDJ said:**
> Here's my experience so far:

Raid5, 3 drives --> 4 drives

When the new drive or a current drive of the array that's being expanded (--grow) fails...the process halts or continues. Anyways: you'll have a degraded array.

Again I must make an assumption:
A part of the data is on the new drive, depending on where in the process (..%) one of the drives failed.

I guess this means that during a grow it seems to convert immediately to a 4 drive RAID 5 (in your example), with the correct parity and everything. This should mean it's safe to stress the drives, as the risks involved when a drive fails are practically the same.

---

