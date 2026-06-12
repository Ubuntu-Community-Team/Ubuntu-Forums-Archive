---
title: "Kernel src build: kernel.org easy, Ubuntu src not; fixed in Feisty?"
date: 2007-06-10
forum: General Help
---

### Post by mattengland on 2007-06-10
Summary:

I've rebuilt my Ubuntu kernels from kernel.org in the past, following the wonderful Master Kernel Thread: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) .  I did this in part because the "standard" Ubuntu kernel-src-package methods just didn't work, or didn't make sense (eg, kernel sources did not match up with headers or binaries...or something like that).

I'd like to try a "stock Ubuntu"-based install in hopes that I don't have to futz around getting the right kernel rev/patches/etc figured out (via a long trial-and-error process) from the kernel.org sources to play nicely with my Feisty distro.  Past experience taught me not to do this, however, and be forced to trudge through the trial-and-error hunting from kernel.org.

The basic question: is this "Ubuntu stock kernel build" process better with Feisty 7.04 (which I just loaded on my laptop)?  Got proof of that?

Details:

My past experiences with custom-kernel builds (to do things like fix the USB driver so I could get my EVDO stuff to work, dual-process config stuff, etc) and Ubuntu taught me this:

Get the kernel src from kernel.org, which puts all the src code in a one (seemingly) clean-and-easy-to-manage directory, I build off a .config I control (or at least can make and easily find), the directions are standard and although somewhat complex, said directions are portable across many systems/platforms/distros.

On the other hand, when trying to rebuild the "stock" kernel with an Ubuntu distro (I tried it with 6.06 and maybe some other rev in the past), things were not "clean-and-easy", trying to match the exact source to the exact installed kernel I had seemed to be exceeding complex and/or difficult (and why the heck was that??)...and it's something that just left a very poor impression.

Now I just loaded a fresh Feisty distro on my laptop (Thinkpad T41).  Now I'm hoping:  has someone "fixed" these problems I experienced (presuming others can empathize with what I describe) and possibly made an easier kernel build experience from the stock kernel/config with Feisty 7.04?

I ask, because I'm hoping to have to save a bunch of time having to fiddle around with a kernel.org build to figure out which rev of kernel and changes/patches are required to make the stuff work and get optimized on my system--and play nicely with Ubuntu.  This is a time-consuming endeavor, but at least it's possible; last time I tried a 6.06 kernel build from the Ubuntu-managed sources/process/structure (which didn't seem to be documented nicely, either, at least nothing like the clean-and-concise-and-popular Master Kernel Thread: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) ), it was nearly impossible to figure out.

Thoughts?

---

### Post by mattengland on 2007-06-23
I'm still interested if anyone can shed any light on this.

Also, I've switched from Feisty to Dapper due to significant ext3 file-system problems as per:
[http://ubuntuforums.org/showthread.php?t=470429](http://ubuntuforums.org/showthread.php?t=470429)

---

### Post by mattengland on 2007-06-25
I'm still looking for perspective on this issue.  As mentioned, I can't run Feisty and have reverted to Dapper due to [this issue](http://ubuntuforums.org/showthread.php?t=470429).

Note that I'd specifically like to update the Dapper kernel with EVDO support (which I've done with later kernels in previous work) and am waiting to do so (ie, trying to see if I can use Ubuntu-based kernel source rather than kernel.org source) until I get authoritative word on this thread.

Thanks for any help.

---

### Post by mattengland on 2007-07-03
I'm still looking for feedback on this topic.  Thanks for any help.

---

### Post by mattengland on 2007-10-21
bump.

---

