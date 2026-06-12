---
title: "Which kernel.org kernels for which ubuntu releases"
date: 2008-01-21
forum: General Help
---

### Post by dariusq2km on 2008-01-21
First, if these are stupid newby kinds of questions, i sincerely apologise, but I haven't been able to find any definitive answers as yet;

How might I find out which ***unpatched kernel.org kernels*** (if any) should work with each release of ubuntu (old or new releases)?

I guess another way of putting this question might be to ask; Which features in each ubuntu release depend on patches to a particular set of kernel.org kernels (ie. so that, if patches weren't applied, those higher-level features would be broken).

**Perhaps the correct answer is '*none*'!** If so, then is it a question of obtaining all the kernel patches for a release and figuring out which kernel.org kernels can have these patches applied without errors?

Could ask this question of *any* linux distro I guess. Perhaps there is a way of automating the creation of a table, based on distro-specific kernel patches. But would anyone benefit from the existence of a lookup table of distro releases and their compatible kernels? (I'd be interested to see such a table, especially if I wanted a kernel feature that wasn't provided with the distro's kernels.)

Finally, looking at the ubuntu kernel source for Fiesty (7.04), am I right in assuming that all ubuntu specific patches are located in the 'ubuntu' directory in the root of the source tree?

Thanks ( for your patience! :/ ) and for any constructive info/thoughts you have about this,

Darius

---

### Post by rufius on 2008-01-21
The corresponding kernel would be whatever the first 3 digit sets of "uname -r" returns.

For example: 
```

zbrown[~]$ uname -r
2.6.22-14-generic

```

In this case, 2.6.22 is the kernel version, 14 is the ubuntu version (modifications via patches), and generic tells which "patch set" was applied. 

Technically all kernels newer than that which is released with the release should *work* since they should be backwards compatible (mostly). As to whether they'll work perfectly is another story. 

There's also the consideration of the patching. I don't know how heavily patched ubuntu's kernel is (never got curious enough to check), but I'd bet its moderately patched. Without those patches you may get "undefined behavior" from the system but I doubt anything catastrophic would occur. You may even get no issues.

I'm not sure the table would really benefit since you can just look (as shown above) what kernel version it is and merely download and configure it.

As to the "ubuntu" directory in the kernel source, your guess is as good as mine but I'd say thats a good place to start.

Hope that helps :)

---

### Post by dariusq2km on 2008-02-02
Thanks Rufius. That's a very helpful general answer.

It seems I could start using the ubuntu 8.04 kernel (2.6.24-5) on my 7.04 system (currently kernel 2.6.20-16) and expect no significant problems. Looking at the kernel dependencies in Synaptic suggests that very little of ubuntu depends on kernel specifics.

What if I want to try Xen? I would guess my 7.04 system can only use those kernels later than my 7.04 kernel, as long as they can be patched with Xen's kernel patches. Strangely though, I see that the package 'xen-image-2.6.19-4-generic' has version '2.6.19-2ubuntu71', which I'm guessing means that it is based on a kernel earlier than that supplied with ubuntu 7.04 but can be used with ubuntu 7.1 (perhaps the xen package developer chose to backport ubuntu 7.1 kernel patches to a pre-7.04 kernel because of better stablity or features of Xen patches ...??)

It's a bit confusing for outsiders. Perhaps I'm assigning to much importance to trying to keep dependencies straight, but how else should one attempt to maintain a stable system?

Thanks again,

Darius

---

