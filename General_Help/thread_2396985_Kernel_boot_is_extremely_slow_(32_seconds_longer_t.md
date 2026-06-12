---
title: "Kernel boot is extremely slow (32 seconds longer than it should be!)"
date: 2018-07-23
forum: General Help
---

### Post by goatboy73 on 2018-07-23
Hi!

I have an Ubuntu Bionic on a self-assembled PC (ASUS Rampage V Extreme, Intel Core i7 5930K, 64GB Quad-channel DDR4-2133MHz DRAM, nVidia GTX 1080Ti using nVidia drivers, Samsung 960 Pro NVME boot drive, all-ssd, etc.), but I have a weird problem: it takes over 70 seconds to boot Linux.  The system is dual-boot using GRUB, with Secure mode enabled (the problem happens even when not using Secure boot). Windows boots much faster (~30 seconds), also from the NVME drive.

So here's my quesiton:

Using some GRUB parameter trickery (i.e. from [here]("https://wiki.ubuntu.com/DebuggingKernelBoot")) I was able to determine that the gap happens at this point during boot (marked with arrows on the left):

```
 
...
      [   14.874357] systemd-udevd[206]: passed 293 byte device to netlink monitor 0x560643931950
      [   14.874613] systemd-udevd[225]: created db file '/run/udev/data/c189:8' for '/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10.4'
      [   14.874628] systemd-udevd[225]: passed device to netlink monitor 0x560643944990
      [   14.877808] systemd-udevd[206]: passed 291 byte device to netlink monitor 0x560643931950
      [   14.943981] raid6: sse2x1   gen()  8340 MB/s
      [   14.991981] raid6: sse2x1   xor()  5364 MB/s
      [   15.039982] raid6: sse2x2   gen() 11296 MB/s
      [   15.087980] raid6: sse2x2   xor()  7211 MB/s
      [   15.135983] raid6: sse2x4   gen() 10926 MB/s
      [   15.183983] raid6: sse2x4   xor()  7237 MB/s
      [   15.231982] raid6: avx2x1   gen() 18857 MB/s
      [   15.279982] raid6: avx2x1   xor() 11654 MB/s
      [   15.327982] raid6: avx2x2   gen() 21305 MB/s
      [   15.375980] raid6: avx2x2   xor() 12925 MB/s
      [   15.423981] raid6: avx2x4   gen() 23815 MB/s
      [   15.471981] raid6: avx2x4   xor() 14393 MB/s
      [   15.473539] raid6: using algorithm avx2x4 gen() 23815 MB/s
      [   15.475097] raid6: .... xor() 14393 MB/s, rmw enabled
      [   15.476659] raid6: using avx2x2 recovery algorithm
      [   15.479098] xor: automatically using best checksumming function   avx
====> [   15.481526] async_tx: api initialized (async)
====> [   47.056620] systemd-udevd[420]: Successfully forked off '(spawn)' as PID 423.
      [   47.056931] systemd-udevd[421]: Successfully forked off '(spawn)' as PID 425.
      [   47.057105] systemd-udevd[422]: Successfully forked off '(spawn)' as PID 427.
...
```

I've attached the full dmesg log, as well as a copy of the SVG generated from running:

```
$ sudo systemd-analyze plot
```

I'm afraid I'm drawing a blank as to how to produce more information in hopes of identifying where those ~32 seconds of "hurry up and wait" are coming from.  I'd like some help in either:


[LIST=1]
[*]Fixing my problem (ha!! of course...but maybe someone out there knows what's going on and can offer a quick fix)
[*]Additional information that may help me further debug the kernel boot cycle (so I can continue to work the problem)
[/LIST]

The reason I'd like the booting to be quicker is because this is a dual-boot box, and I'm starting to get annoyed at the super-slow Linux boot time, especially when I see my laptop boot up in 25 seconds running the same Ubuntu release.  I guess the "big box" simply likes to take its time.

Some additional tidbits:


[LIST]
[*]There ***is*** a RAID array in play, but it's not a factor as I've disabled it and the delay is still there
[*]The nVidia drivers are also cleared as the culprits since the boot delay happens even when they're not present in the system (at all... apt-get ***purge***-d)
[/LIST]

Any help or suggestions will be greatly appreciated!

Thanks!

---

### Post by monkeybrain20122 on 2018-07-24
it may be this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1779961") in kernel 4.15.0-24. You can check by booting into kernel 4.15.0-23 (press esc or shift when boot to see the grub screen, choose advanced options and choose the older kernel) and see if it still takes that long.

If confirm it is the bad kernel, see post 14 in[ this thread]("https://ubuntuforums.org/showthread.php?t=2395459&page=2") for the simple workaround.

---

### Post by goatboy73 on 2018-07-29
Thanks for the info! It was actually an issue with the hibernate/resume configuration.  My computer has TONS of RAM, so I haven't used a swapfile for ages.  However, the file **/etc/initramfs-tools/conf.d/resume** still contained a reference (partition UUID) to the swap partition that was created upon system installation a long time ago, but no longer existed:

```
RESUME=65915d16-c817-423e-b340-115d886aa758
```

The result was that the boot process was ***timing out ***(by 32 seconds!!) when looking for that partition during boot. By changing that to read:

```
RESUME=none
```

Things immediately improved by those ~32 seconds.  It's still slower than I'd like, but I can live with a 30 second boot-time considering all the crap this computer has to initialize (including the nVidia drivers).

Thanks!

---

### Post by Yellow Pasque on 2018-07-30
30s still seems fairly slow for an SSD boot. My old Debian system (Athlon X2, 2GB RAM) takes about 6s off a SanDisk UltraII SSD.

> all the crap this computer has to initialize (including the nVidia drivers).

I'm not sure why you think the nvidia drivers would significantly add to the boot time as opposed to any other video driver.

---

