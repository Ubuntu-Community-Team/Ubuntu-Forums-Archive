---
title: "Kernel Configuration suggestions"
date: 2014-01-02
forum: General Help
---

### Post by Tristan_Williams on 2014-01-02
This is for myself, plus all the other people who, like me, have no idea which kernel configurations offer the greatest performance increase.

Here are the ones I usually do:

Under Processor type and features:

Select the correct processor type (for some reason it always resets to Intel Pentium-pro, which i DO NOT have)
Disable Generic x86 support (only do this if kernel recognizes your particular processor)
Under Processor Vendors, disable all except the one that applies to me.
Preemption Model = Preemtable Kernel (Low-Latency Desktop)

Basically disable anything that doesn't apply to my particular processor (Intel Core 2 duo)

And under Networking:

Disable amateur radio support



So what other options offer significant performance increases?

---

### Post by tgalati4 on 2014-01-03
If you don't understand all of the kernel options, you will most likely have a broken kernel.  Basically, the stock kernel configuration will provide high performance.  I read an article about Gentoo (where you have to compile a custom kernel) achieves a 2% increase in performance.  Are there gains bigger than that?  Probably, but only for specific workloads, and most of the scheduling and kernel tweaks can be done in User Space using *sysctl *.

Removing stuff that you don't have (like ham radio support) will make the kernel smaller.

-rw-r--r--  1 root root  5129040 Nov 27  2012 vmlinuz-3.5.0-17-generic
-rw-------  1 root root  5134032 Jan 24  2013 vmlinuz-3.5.0-23-generic
-rw-------  1 root root  5138448 Feb 25  2013 vmlinuz-3.5.0-25-generic
-rw-------  1 root root  5124624 Mar  8  2013 vmlinuz-3.5.0-26-generic
-rw-------  1 root root  5127408 Mar 25  2013 vmlinuz-3.5.0-27-generic
-rw-------  1 root root  5131856 Aug 13 11:56 vmlinuz-3.5.0-39-generic

5.13 MB for kernel 3.5 for instance.  Your RAM footprint will also be slightly smaller by eliminating modules and parts that you don't need.  Will this result in a performance increase?  Perhaps--2%.

Selecting low-latency desktop means you will have a draggy mouse--with more CPU cycles going to finish tasks than handle user input.

You haven't described the workloads or performance measurements for those workloads to know if your custom kernel is having any impact.

---

