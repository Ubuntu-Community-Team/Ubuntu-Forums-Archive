---
title: "System hangs on &quot;waiting for root file system&quot;"
date: 2008-02-03
forum: General Help
---

### Post by andymushu on 2008-02-03
When my computer boots, on the usplash screen it says "waiting for root file system". Unlike almost all threads i have found on this, my computer continues to boot. It just takes about 30 seconds longer than it actually should. This problem started when i added a sata hard drive to my then-all IDE configuration. now my only hard drive is sata, with no ide drives left in the system, and the error continues. Unlike many other threads i have seen on this issue, i did not upgrade to a new release of ubuntu or upgrade my kernel, or even do anything remotely of that sort. Any advice on how to eliminate this uncharacteristically long boot time caused by this issue would be greatly appreciated.

---

### Post by andymushu on 2008-02-04
anyone?

---

### Post by irieken on 2008-02-23
> **andymushu said:**
> anyone?

In this post: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123)
I found a message by Alf Lervåg that was very helpful.

The gist was this: When you get dropped to Busy Box prompt, type in:
modprobe ide-disk; modprobe ide-generic; cat /sys/block/hda/dev; mknod /dev/hda1 b 3 0

Then press ctrl+D, and your machine will boot!

So, once you figure out what's causing the problem, you'll be able to fix it from inside the OS.... Unfortunately, I don't know how to actually fix the problem:(

---

### Post by andymushu on 2008-02-24
thanks for the help, but that was never the issue. i was never dropped to a busybox prompt. the system would boot, it would just take ridiculously long. apparently i fixed it now, by disabling the unused IDE interfaces in my BIOS.

---

