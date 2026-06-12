---
title: "'stripe=32742' Root FS Mount Option after Kernel Upgrade"
date: 2017-12-11
forum: General Help
---

### Post by mdt1024 on 2017-12-11
Hello All,

I recently update/upgraded eight hosts.  Seven of them have their ext4 root filesystem (/dev/xvda) mounted with the same options that they had before the upgrade, namely:

(rw,relatime,errors=remount-ro,data=ordered)

One of them came up with:

(rw,relatime,errors=remount-ro,stripe=32742,data=ordered)

On this one, host dmesg shows two messages related to mounting root:
[   19.799108] EXT4-fs (xvda): mounted filesystem with ordered data mode. Opts: (null)
[  117.242727] EXT4-fs (xvda): re-mounted. Opts: errors=remount-ro

It states nothing about 'stripe=32742'.  I see in 'man mount 8' that:

stripe=n  Number  of  filesystem  blocks  that mballoc will try to use for allocation size and
              alignment.  For RAID5/6 systems this should be the number of data disks * RAID chunk
              size in filesystem blocks.

I fail to see why this would need to be set to 32742.  Any insights would be appreciated =)

Thanks!

Marshall

---

### Post by mdt1024 on 2017-12-19
I'm in the "Repliers to Myself Club" here:)  

I did find this similar unanswered post titled "Why is 'stripe=4' mount option specified by default for /boot?":

[https://bbs.archlinux.org/viewtopic.php?id=176092](https://bbs.archlinux.org/viewtopic.php?id=176092)

This leads me to believe that the answer is not trivial.  I am no closer to finding a solution except to tell my monitoring system that it is 'OK'.

One thing I did find in dmesg that I don't really understand given that this host does not use RAID:

[206439.972069] raid6: sse2x1   gen()  6274 MB/s
[206440.049511] raid6: sse2x1   xor()  4857 MB/s
[206440.116018] raid6: sse2x2   gen() 10101 MB/s
[206440.184032] raid6: sse2x2   xor()  6399 MB/s
[206440.252085] raid6: sse2x4   gen() 11654 MB/s
[206440.320084] raid6: sse2x4   xor()  5899 MB/s
[206440.320088] raid6: using algorithm sse2x4 gen() 11654 MB/s
[206440.320091] raid6: .... xor() 5899 MB/s, rmw enabled
[206440.320093] raid6: using ssse3x2 recovery algorithm
[206440.348263] xor: automatically using best checksumming function:
[206440.388014]    avx       :  3719.000 MB/sec
[206440.451191] Btrfs loaded

Related?  Dunno...

---

