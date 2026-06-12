---
title: "floating point exception (core dumped) - btrfs rescue chunk-recover"
date: 2016-01-06
forum: General Help
---

### Post by prshah on 2016-01-06
Hello,

TL;DR ==


btrfs 3x500GB RAID 5 - One device failed. Added a new device (btrfs device add) 
and tried to remove the failed device (btrfs device delete).

I tried to mount the array in degraded mode, but that didn't work either. After 
multiple attempts (including adding back the failed HDD), I finally ran the 
btrfs rescue chunk-recover command on the primary member /dev/sdb.

This ran for about 4 hours, and then failed with "floating point exception (core 
dumped)".
==

I am testing out btrfs to gain familiarity with it. I am quite amazed at it's 
capabilities and performance. However, I am either not able to understand or 
implement RAID5 fault tolerance.

I understand from the wiki that RAID56 is experimental. The data I am working 
with is backed up elsewhere and for all intents and purposes, discard-able.

I have set up a btrfs RAID5 with 3x500GB Seagate HDDs, with a mount point of 
/storage. Booting is off a fourth HDD (ext4, lubuntu 64bit) that is not 
involved in the RAID.

Everything was working amazingly well, until one HDD failed and was quietly 
offlined. For a couple of days, the RAID was running off 2 HDDs and I didn't 
notice.

When I DID realize, I shut down the system, bought a new HDD (2TB), which took 
a couple of days to arrive.

When I powered up the system again, the failed 500GB was back. Everything 
loaded fine, and looked good. To be on the safe side, I ran a badblocks test 
(ro) on the failing HDD.

Halfway through the test, the HDD disappeared again. After a cold reboot, it 
was loaded fine again.

At this point, I decided to replace the failed HDD. I shutdown, plugged in the 
new HDD in place of the boot HDD, booted up with Lubuntu live, mounted 
(/storage) and added the device to the RAID.

After adding the device successfully, I gave a device delete command for the 
failed HDD. Partway through the process, the failing HDD (/dev/sdc) disappeared 
again, and after waiting a couple of hours, I hard-reset the system, and 
removed the failing HDD, assuming that the RAID will re-build on the existing 
devices.

Now, the RAID (/storage) refused to mount. I got a c_tree error (please see 
enclosed logs below).

I tried to mount the array in degraded mode, but that didn't work either. After 
multiple attempts (including adding back the failed HDD), I finally ran the 
btrfs rescue chunk-recover command on the primary member /dev/sdb.

This ran for about 4 hours, and then failed with "floating point exception (core 
dumped)".

Can I recover the array or should I start again? The data is not important, but 
I would like to know the recovery process, or any misconceptions in my thinking 
that RAID5 with 3 devices is enough for SOHO-level fault tolerance?

Any advice, pointers, etc, much appreciated. Tech level: medium-high (RHCE).

Relevant system information:
=== uname -a
Linux lubuntu 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 
x86_64 x86_64 x86_64 GNU/Linux


== btrfs --version
btrfs-progs v4.0

== btrfs fi show
warning, device 2 is missing
Label: 'storage'  uuid: 5a3d6590-df08-4520-b61b-802d350849c7
        Total devices 4 FS bytes used 176.91GiB
        devid    1 size 465.76GiB used 90.03GiB path /dev/sdb
        devid    3 size 465.76GiB used 90.01GiB path /dev/sdc
        devid    4 size 1.82TiB used 10.00GiB path /dev/sda
        *** Some devices missing

== dmesg info
...
Jan  5 01:45:22 lubuntu kernel: [   10.338295] Btrfs loaded
Jan  5 01:45:22 lubuntu kernel: [   10.338899] BTRFS: device label storage 
devid 4 transid 969 /dev/sda
Jan  5 01:45:22 lubuntu kernel: [   10.340448] BTRFS info (device sda): disk 
space caching is enabled
Jan  5 01:45:22 lubuntu kernel: [   10.340454] BTRFS: has skinny extents
Jan  5 01:45:22 lubuntu kernel: [   10.343395] BTRFS: failed to read the system 
array on sda
Jan  5 01:45:22 lubuntu kernel: [   10.352137] BTRFS: open_ctree failed
Jan  5 01:45:22 lubuntu kernel: [   10.382199] BTRFS: device label storage 
devid 1 transid 969 /dev/sdb
Jan  5 01:45:22 lubuntu kernel: [   10.383740] BTRFS info (device sdb): disk 
space caching is enabled
Jan  5 01:45:22 lubuntu kernel: [   10.383744] BTRFS: has skinny extents
Jan  5 01:45:22 lubuntu kernel: [   10.384469] BTRFS: failed to read the system 
array on sdb
Jan  5 01:45:22 lubuntu kernel: [   10.392116] BTRFS: open_ctree failed
Jan  5 01:45:22 lubuntu kernel: [   10.423075] BTRFS: device label storage 
devid 3 transid

... // after btrfs rescue chunk for about 4 hours
Jan  5 06:01:45 lubuntu kernel: [15404.828156] traps: btrfs[3016] trap divide 
error ip:4211a0 sp:7ffd7dbb03a8 error:0 in btrfs[400000+73000]
...

== some output from btrfs rescu chunk -vv
...
            Stripes list:
            [ 0] Stripe: devid = 3, offset = 21484273664
            [ 1] Stripe: devid = 2, offset = 21484273664
            [ 2] Stripe: devid = 1, offset = 21504196608
        Chunk: start = 45134905344, len = 2147483648, type = 81, num_stripes = 3
            Stripes list:
            [ 0] Stripe: devid = 3, offset = 22558015488
            [ 1] Stripe: devid = 2, offset = 22558015488
            [ 2] Stripe: devid = 1, offset = 22577938432
        Chunk: start = 47282388992, len = 2147483648, type = 81, num_stripes = 3
            Stripes list:
            [ 0] Stripe: devid = 3, offset = 23631757312
            [ 1] Stripe: devid = 2, offset = 23631757312
            [ 2] Stripe: devid = 1, offset = 23651680256
...
        Device extent: devid = 4, start = 5369757696, len = 1073741824, chunk 
offset = 201901211648
        Device extent: devid = 4, start = 6443499520, len = 1073741824, chunk 
offset = 204048695296
        Device extent: devid = 4, start = 7517241344, len = 1073741824, chunk 
offset = 206196178944
        Device extent: devid = 4, start = 8590983168, len = 1073741824, chunk 
offset = 208343662592
// floating point error

Regards,
PRShah

---

