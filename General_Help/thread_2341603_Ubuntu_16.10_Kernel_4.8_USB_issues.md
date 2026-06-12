---
title: "Ubuntu 16.10 Kernel 4.8 USB issues"
date: 2016-10-29
forum: General Help
---

### Post by edwardecl on 2016-10-29
I just updated to Ubuntu 16.10 assuming any of the newer kernel issues would have been sorted out.

But there is one major problem, if I used a USB audio device with kernel 4.8 after logging in all my USB devices disappear including the mouse and keyboard. Done some of my own searching on other forums and it's a known issue with kernel 4.8, one post tells you how to fix it but obviously it requires recompiling the kernel I assume.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1630063](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1630063)

Any ideas when the fix will be pushed to Ubuntu 16.10?

---

### Post by Dread Knight on 2016-10-31
This is ultra annoying. It's like Ubuntu 16.10 hasn't even been tested. Luckily I use Ubuntu for lots of years and I know how to pick an older kernel at boot time, which works for me, provided I don't constantly forget to do that thing.

---

### Post by edwardecl on 2016-11-13
I guess it's not on the priority to fix list then, done a few kernel updates since then and still broken.

---

### Post by jonandtice on 2016-11-29
My USB audio interface kept disappearing at the same time my computer was freezing... except it wasn't freezing, I was just loosing my mouse and keyboard. As far as I can tell, it's a problem with USB 3.0 ports. So the solution is to either not use 3.0 ports or install a 4.7 kernel (and would have to select every time at boot) or a 4.9 kernel. They can be downloaded from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). You will have to install the linux-headers...all, linux-headers...generic and linux-image...generic.

---

### Post by edwardecl on 2016-12-14
I don't have any USB 3.0 devices nor do I have anything plugged into USB 3.0 ports so it's not that.

If I just leave my USB audio device plugged in it randomly shuts all the USB ports down, sometimes on the login screen, sometimes minutes after logging in, always when you try and play audio after 10 seconds.

I know the older Kernel is fine, but the issue should have been patched in 4.8 so why not update the official repo with the bug fix? It's quite a severe bug. And didn't they want to update the LTS release to this kernel, should be fun.

---

### Post by bob brazie on 2017-02-27
MY system would freeze when going to suspend. Had to hard boot and it wouldn't find a system to boot into. Had to re-install every time.
Happened on 16.04.1, 16.04.2 and 16.10 when using the 4.8 Kernel.
Went back to plain 16.04 with the old kernel and it is working as it should.
Not sure why this problem got through or what the fix would be.

---

